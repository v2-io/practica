# §3 — The structural identification, AAT side (draft)

*First draft, sets voice/depth/citation-density precedent for the rest of the paper. To iterate.*

---

Adaptation and Actuation Theory (AAT) is a formal framework for adaptive agents under bounded resources and unreliable observation. It supplies a vocabulary for *what* an agent must do to keep its beliefs aligned with reality, *how fast* it must do it, and *under what conditions* a composite of multiple agents can be treated as one agent. We are not introducing AAT here — only the small subset that bears on practica's structural identity. Two AAT results are load-bearing: the **wrapping construction**, which formalizes how an agent system can recover certain structural guarantees its components lack, and the **orient cascade**, which formalizes how an adaptive agent should resolve mismatch between its model and reality. The wrapping construction is presented in §3.2–3.4; the orient cascade is recovered in §3.5 as a *consequence* of the wrapping rather than as a parallel structure.

## 3.1 The architectural classification: why Class 3 substrates are the hard case

AAT classifies adaptive agents by whether goal-state can causally influence belief-update processing within the agent's architecture[^class-classification]. The classification is structural — a property of the agent's processing topology, not a tunable parameter:

- **Class 1 (Separated).** Belief-update and goal-conditioning live in causally distinct processing pathways. A Kalman filter feeding a Linear-Quadratic-Regulator is the canonical example; the filter's belief-update has no causal path from the controller's objective.
- **Class 2 (Partial).** Some processing pathways are separated, some are merged. Biological cortex with separate sensory and prefrontal areas is the canonical example.
- **Class 3 (Coupled).** A single mechanism handles both belief-update and goal-conditioned processing. *Transformer LLMs are the canonical Class 3 substrate*: attention processes the query (often containing the goal) and the observation together in a single forward pass[^class-3-llms].

The distinction matters because AAT's central machinery for adaptive resolution — the orient cascade, the sequential resolution of mismatch types, the persistence theorems — is derived under Class 1 conditions. Class 3 substrates fail directed-separation by construction[^directed-separation-fails]: belief-update and goal-conditioning are *not* causally separable when both live in the same forward pass. The Class 1 results do not transfer to Class 3 components directly.

This is the problem any system whose components are LLMs must solve at the system level, because it cannot be solved at the component level.

[^class-classification]: `~/src/agentic-systems/01-aat-core/src/der-directed-separation.md` §"Architectural classification": *"Whether directed separation holds is determined by the agent's **processing topology** — specifically, whether $G_t$ is causally upstream of $f_M$ in the agent's internal processing graph. This is a structural property of the architecture, not a tunable parameter."*

[^class-3-llms]: Same source, table at §"Architectural classification": Class 3 (Coupled) examples include *"Transformer LLM (attention processes goals and observations together)."* The structural-coupling property of decoder-only transformer attention is formalized at lemma grade in a companion technical paper (NeurIPS 2026 Paper 3, `~/src/neurips/03-llm-hallucinate-bound/`), with extensions to linear attention / Mamba / state-space models under a per-source non-degeneracy condition.

[^directed-separation-fails]: Same source, §"Implications for theory scope": *"Class 3 (Coupled): Requires coupled formulation from the start — $X_{\tau^+} = f_X(X_{\tau^-}, e_\tau)$ without decomposition. This is the scope of `03-llm-core/`."* Section II's Class 1 results do not apply.

## 3.2 The wrapping construction

The wrapping construction[^wrapping-source] addresses the Class 3 problem at the *system* level rather than at the component level. Wrap the Class 3 component inside a scaffold whose own state is structurally typed to enforce the separation the component cannot provide internally.

Concretely, the wrapper $W$ around a primitive component $A$ maintains its own state $X_W = (M_W, G_W)$ — a belief substate $M_W$ and a goal substate $G_W$ — and updates them through *type-signed* operations:

- A **belief-side query selector** $q_M : \mathcal{X}_M \times \mathcal{O}_W \to \mathcal{Q}_A$ chooses what to ask the component for the belief-update. *It has no $G_W$ argument by type signature.*
- A **belief-update map** $f_M : \mathcal{X}_M \times \mathcal{O}_W \times \mathcal{Q}_A \times \mathcal{O}_A \to \mathcal{X}_M$ updates the belief substate. *It also has no $G_W$ argument by type signature.*
- A **strategy-side query selector** $q_G$ and a **strategy-update map** $f_G$ — both *do* depend on $G_W$ — handle the goal-conditioned work.

The structural commitment is in the type signatures: the belief-update path *cannot* see $G_W$ regardless of what the component would do if asked. The wrapper's belief-update is therefore goal-blind by construction[^by-construction-quote].

The construction admits three regimes, distinguished by where structural separation lives[^regime-hierarchy]:

| Regime | Construction | Leakage bound | Bound source |
|---|---|---|---|
| **W₀** | No wrapping; raw Class 2/3 component | Component's maximum goal-conditioning sensitivity | None — no constraint |
| **W₂** | Partial wrapping: one goal-conditioned call per macro-step; structured parsing of the response into $M_W$ vs $G_W$ slots | **Behavioral** — bounded by the component's instruction-following fidelity | Component's compliance with the prompted instruction-to-separate |
| **W₁** | Strict wrapping: separate $q_M$ and $q_G$ calls per macro-step | **Structural** — bounded by $I(A(q_M); G_W \mid q_M)$ in the pretraining distribution | Pretraining-induced query-content / goal-content correlation |

The hierarchy is monotone: W₀ → W₂ → W₁ moves the *kind* of bound from "no bound" to "behavioral" to "structural." Practical scaffolded-LLM frameworks (ReAct, Reflexion, MemGPT, Generative Agents' observation→memory step) almost universally implement W₂: *the wrapper exists, but the query boundary still passes goals to the component, and only the response parsing enforces type separation*[^practical-w2].

[^wrapping-source]: `~/src/agentic-systems/01-aat-core/src/der-class-coercion-via-wrapping.md` — the canonical home segment. Status: derived/conditional under admissibility conditions (C1)–(C3) on the component.

[^by-construction-quote]: Same source, *[Definition (wrapper-update-maps)]*: *"Belief-side query selector: $q_M : \mathcal{X}_M \times \mathcal{O}_W \to \mathcal{Q}_A$. The wrapper chooses the query for $M_W$ updates from belief and observation only — *no $G_W$ argument*."* The "no $G_W$ argument" line, repeated for both $q_M$ and $f_M$, is the structural commitment.

[^regime-hierarchy]: Same source, §"Wrapping regime hierarchy" — table and surrounding text. The three regimes (W₀ / W₂ / W₁) refine the Class 1 (Separated) cell of the architectural classification into "Class-1-by-structure" and "Class-1-by-behavior."

[^practical-w2]: Same source, Working Notes: *"Practical scaffolded-LLM frameworks (ReAct, Reflexion, MemGPT, etc.) almost universally implement W₂. Distinguishing W₂ from W₁ in a deployed system requires inspection of the per-cycle query structure — does $f_M$'s update path receive a query that contains $G_W$ or not? This is the diagnostic question."*

## 3.3 What the wrapping yields

Under three conditions on the component[^admissibility] — (C1) it admits a goal-blind query mode; (C2) its output distribution is stationary during the wrapper's operation; (C3) its response to a goal-blind query does not depend on $G_W$ via inference from query patterns — the wrapping construction yields directed separation at the wrapper level by construction:

$$P(M_{W,m+1} \mid M_{W,m},\ o_{W,m+1},\ G_{W,m}) = P(M_{W,m+1} \mid M_{W,m},\ o_{W,m+1})$$

This is Theorem 1 in the canonical source, and it is *exact*[^theorem-1] under (C1)–(C3). The wrapper is then Class 1 (Separated) at its own level — even though the component is Class 3.

In the realistic case, (C3) holds only approximately: pretrained components encode some correlation between query content and goal content. Theorem 2[^theorem-2] weakens (C3) to a KL-leakage bound $\kappa$, and propagates that bound to the wrapper's belief-update via the data-processing inequality:

$$D_\text{KL}\big(P(M_{W,m+1} \mid M_{W,m}, o_{W,m+1}, G_{W,m})\, \big\Vert\, P(M_{W,m+1} \mid M_{W,m}, o_{W,m+1})\big) \le \kappa$$

The wrapper is then *almost*-Class-1 with leakage rate at most $\kappa$. For strict (W₁) wrapping, $\kappa$ is bounded *structurally* by $I(A(q_M); G_W \mid q_M)$ — a property of the pretraining distribution that does not depend on the deployment.

A second result, established in the companion segment[^composition-segment], shows that the wrapped system is also a *valid AAT composite agent*: under wrapper-design constraints (a commitment to a prediction map; a gain interpretation for $f_M$; a sector condition for the macro-correction[^sector-condition-gloss]), the wrapper inherits AAT's persistence-template — the structural condition $\alpha_W R_W \gt \rho_W$ that governs whether the agent can maintain bounded mismatch under disturbance[^persistence-inequality-gloss].

Both results carry the same epistemic tier: *derived under stated conditions* (the admissibility conditions plus the wrapper-design constraints). The proofs are short — Theorem 1 is conditional-independence reasoning under the type-signed update structure; Theorem 2 is one application of the data-processing inequality. The substantive content is in the conditions and the construction, not in mathematical depth.[^proof-strength]

[^admissibility]: `der-class-coercion-via-wrapping.md` §Conditions: (C1) goal-blind admissibility — *"$\mathcal{Q}_A$ contains queries whose specification can be constructed from $(M_W, o_W)$ alone."* Components partition into Class A (goal-blind by design — POMDP filters, retrieval), Class B (admit a goal-blind mode — LLMs in summarization/fact-extraction modes), Class C (fundamentally goal-conditioned — pure end-to-end policy networks; out of scope for the construction). (C2) stationary component conditional — *"$A$'s output distribution conditional on input is fixed during the wrapper's operation."* (C3) no implicit goal-inference — $P(A(q_M) \mid q_M, G_W) = P(A(q_M) \mid q_M)$ for all $q_M, G_W$.

[^theorem-1]: Same source, Theorem 1 (exact form): *"Under (C1)–(C3), directed separation holds *exactly* at the wrapper level."* The proof identifies the paths from $G_{W,m}$ to $M_{W,m+1}$ given $(M_{W,m}, o_{W,m+1})$: $f_M$ and $q_M$ have no $G_W$ argument by type signature (two pathways closed); (C3) closes the remaining pathway through $A(q_M)$ via conditional independence.

[^theorem-2]: Same source, Theorem 2 (approximate form, C3 weakened to leakage bound): *"If (C3) is replaced by a KL-leakage bound … then the wrapper-level KL-divergence on $M_W$ updates is bounded by the same $\kappa$."* Proof: data-processing inequality applied to the deterministic function from the component's response distribution to the wrapper's state distribution.

[^composition-segment]: `~/src/agentic-systems/01-aat-core/src/der-class-coercion-in-composition.md` — the companion segment establishing composition-level consequences. The wrapper is a valid AAT composite agent under wrapper-design constraints (D-A2)–(D-A4); inherits sector-persistence template; pays Brooks's-Law tempo cost (§3.4 below).

[^sector-condition-gloss]: *Sector condition* is AAT's name for a bound on how the agent's correction function responds to mismatch. Informally: when the agent observes a difference between what it predicted and what happened, its correction is at least proportional to that difference (up to a saturation point). Formally: $\delta^T F(\delta) \geq \alpha \lVert \delta \rVert^2$ for $\lVert \delta \rVert \leq R$, where $\delta$ is the mismatch signal, $F$ is the correction function, $\alpha > 0$ is the correction rate, and $R$ is the reserve (the saturation radius). Canonical source: `~/src/agentic-systems/01-aat-core/src/result-sector-condition-stability.md`. This paper uses sector-condition language only to point to the precondition the wrapper inherits; the details do not bear on the convergence argument directly.

[^persistence-inequality-gloss]: *Persistence inequality* $\alpha R \gt \rho$ is AAT's structural condition for an adaptive agent to maintain bounded mismatch under environmental disturbance: the agent's correction capacity ($\alpha R$, roughly *rate times reserve*) must exceed the rate at which environmental disturbance accumulates ($\rho$). When the inequality holds, the agent's mismatch stays bounded; when it fails, mismatch grows without bound. The wrapper inherits this inequality at its own level, with $\rho_W$ split into external environmental disturbance plus internal disturbance from the component's response variance. Canonical source: `~/src/agentic-systems/01-aat-core/src/result-sector-persistence-template.md`.

[^proof-strength]: This is not a hedge — the proofs are short *because* the construction has already done the structural work in the type signatures. The substantive content lives in establishing that the type-signed wrapper construction is feasible under the admissibility conditions, not in mathematical depth of the proofs themselves. I would think this difficulty-shifting structure is hard to refute: the work moves into the construction; the proof becomes short *as a result*, not as a sign of shallow content.

## 3.4 Cost: leakage and tempo

The wrapping construction is not free, and the cost is paid in two places.

**Residual leakage.** Even under strict W₁ wrapping, $\kappa \gt 0$ in general — the structural bound $\kappa \le I(A(q_M); G_W \mid q_M)$ is only zero when the pretraining distribution induces no correlation between query content and goal content. For LLM components, this is rarely the case. The wrapper is *almost*-Class-1, not exactly Class-1, in deployment.

**Brooks's-Law tempo cost.** The wrapper makes $K \geq 2$ component calls per macro-step (more in richer wrapper designs)[^brooks-law]. The wrapper's macro-update rate is therefore at most $\nu_A / K$ where $\nu_A$ is the component's nominal call rate. In AAT's tempo coordinates:

$$\mathcal{T}_W \leq \mathcal{T}_A^\text{nominal} - C_\text{coord}^\text{wrap}$$

where $C_\text{coord}^\text{wrap}$ is the coordination overhead specific to the wrapping construction. The wrapped system runs *slower* than the raw component — by a structurally determined factor. This is the same Brooks's-Law form that governs all AAT compositions; the wrapping construction does not escape it.

The wrapped system's persistence at the wrapper level requires the persistence inequality to hold *after* paying these costs: $\alpha_W R_W \gt \rho_\text{ext} + \rho_\text{int}$, where $\rho_\text{int}$ is bounded by the variance of the component's responses to goal-blind queries. The wrapping construction moves the structural locus from "the component is trustworthy" to "the wrapper's $(\alpha, R, \rho)$ parameters satisfy the persistence inequality." Whichever way one frames it, *something* must satisfy the inequality. The wrapping does not produce trust from nothing.

[^brooks-law]: `der-class-coercion-in-composition.md` §"Tempo cost — Brooks's-Law instance": *"The wrapper makes $K \geq 2$ component calls per macro-step (more in richer wrapper designs). If the component's nominal call rate is $\nu_A$, the wrapper-level macro-update rate is $\nu_W = \nu_A / K$."* The Brooks's-Law form is derived in `#der-tempo-composition`. The phrase "Brooks's Law as derived inequality" appears elsewhere in the canon as well, with the qualitative claim (a sharp coordination-overhead threshold) more robust than any specific numerical constant.

## 3.5 Two readings of the same construction

The wrapping construction performs two distinct functions for a system using a Class 3 substrate. Reading the construction with each function in mind illuminates what the wrapping is *for*.

**Reading 1: Truthification.** The wrapping construction moves the system from W₀ (unwrapped Class 3) toward W₁ (strict wrapping with structural leakage bound). The W₀/W₂/W₁ hierarchy is the *graded* characterization of how thoroughly the structural separation has been applied[^truthification-named]. AAT names this *truthification*: the wrapping construction is *"the rigorous formal version"* of what informal defensive scaffolding has been doing for decades — peer review, prediction registers, double-entry bookkeeping, structured red-teaming. All share the same discipline: a goal-blind belief-update query path is structurally enforced (W₁) or behaviorally bounded (W₂), at a definite cost in tempo overhead plus a residual leakage rate.

**Reading 2: Cascade-recovery.** AAT's orient cascade[^orient-cascade] is the formal name for how a Class 1 (Separated) adaptive agent resolves mismatch between model and reality. The cascade has a specific information-dependency-forced ordering: epistemic update first ($M_t$), then attainability assessment ($A_O$), then strategy evaluation ($\Sigma_t$), then objective revision ($O_t$) *last*. The ordering is exact — forced by which quantities appear in which formulas[^cascade-exact]. *Class 3 substrates cannot produce this ordering internally* because the steps live in one merged forward pass; the resolution-order cannot be separated from the parallel composition[^cascade-internal]. Once the wrapping construction recovers Class 1 status at the wrapper level, the orient cascade applies at the wrapper level. The scaffold reproduces externally what the substrate cannot produce internally.

These are not two independent results. They are two functions performed by the same construction. Reading 1 emphasizes *what the wrapping yields* — directed separation, the substrate of truthification. Reading 2 emphasizes *what becomes possible* once the wrapping has yielded it — the cascade applies. For a system whose components are Class 3 substrates, both functions are non-substitutable: without the wrapping, neither directed separation nor the cascade can operate at the wrapper level.

This is the structural job, in AAT vocabulary: *recover Class 1 status at the wrapper level by structural commitment of the type signatures, paying a tempo cost and a residual leakage cost, so that the AAT machinery (persistence template, orient cascade, sector condition) applies at the wrapper level rather than at the component level*. The same construction is named two different ways depending on which function one foregrounds.

[^truthification-named]: `der-class-coercion-via-wrapping.md` §"Wrapping as a truthification mechanism": *"The wrapping construction is the *rigorous formal version* of what `#disc-adversarial-coupling-pressure` §'Defensive scaffolding as composition' gestures at informally — peer review, prediction registers, double-entry bookkeeping, adversarial procedure, structured red-teaming."* And: *"The W₀/W₂/W₁ regime hierarchy is the *graded* characterization of how thoroughly the truthification has been applied — W₀ is the un-truthified base state, W₂ behavioral truthification, W₁ structural truthification."*

[^orient-cascade]: `~/src/agentic-systems/01-aat-core/src/der-orient-cascade.md` — canonical home segment, status `claims-verified`. *"$M_t \to A_O \to \Sigma_t \to O_t$. The ordering is not a design choice — it's a consequence of which quantities require which others."* The 2×2 diagnostic (satisfaction-gap × control-regret) routes revisions in cascade order; objective-revision is structurally the last resort.

[^cascade-exact]: Same source, Epistemic Status: *"The cascade **ordering** is *exact*: it is a logical consequence of which quantities appear in which formulas."* What is *not* derived is the timing — how long to spend on each step.

[^cascade-internal]: `der-directed-separation.md` §"Implications for theory scope": *"Class 3 (Coupled): Requires coupled formulation from the start … without decomposition."* Combined with the orient-cascade segment's information-dependency-forced ordering, the cascade cannot run inside a Class 3 substrate; it must run at a level where directed separation holds. The wrapping construction is precisely the move that creates such a level.

## 3.6 Two closure-defect quantities, and the *wanted* deviation

A subtle point matters for §4 and §5, because it is easy to mis-read. The wrapping construction *deliberately* changes the underlying component's behavior — that is the *point* of wrapping. The wrapper's externally-observable behavior should differ from the raw component's, because the wrapper has imposed structural separation the component would not have respected.

AAT distinguishes two closure-defect quantities to track this[^two-epsilons]:

- $\varepsilon^*_{\text{track}}$ — the standard fidelity quantity. *How well does the wrapper's macro-description track the underlying micro-dynamics?* Small is good (the wrapper has not lost information about reality). Bounded by AAT's bridge lemma under sector-condition assumptions.
- $\varepsilon^*_{\text{coerce}}$ — the wrapping-specific quantity. *How much does the wrapper's behavior diverge from the unwrapped component?* Large is good — the divergence is the wanted deviation; it is the truthification operation *doing its job*.

The two quantities are conceptually distinct. AAT's source explicitly warns: *"Conflating them propagates downstream confusion."* The same wrapper can have small $\varepsilon^*_{\text{track}}$ (faithful to underlying reality) and large $\varepsilon^*_{\text{coerce}}$ (behaviorally different from the raw component) simultaneously, and *both* are signs of a working wrapper.

This will matter for the engineering side in §4. Operational measurements that conflate *"the wrapper behaves differently from the component"* with *"the wrapper is failing"* will systematically miscategorize working W₁ wrappers as broken. The two-quantity distinction is what makes the operational measurement legible.

[^two-epsilons]: `der-class-coercion-in-composition.md` Discussion §"Coercion-distance vs. tracking-distance": *"$\varepsilon^*_{\text{track}}$ — the standard fidelity quantity from `#form-composition-closure`. Used in the bridge lemma to bound trajectory error. $\varepsilon^*_{\text{coerce}}$ — the wrapping-specific quantity measuring behavioral divergence between the wrapped system and the unwrapped component. Higher means more aggressive coercion."* Repeated in `form-composition-closure.md` Discussion §"Constructive (A1)–(A4) via wrapping": *"The wrapper *deliberately* changes the underlying component's behavior to enforce structural separation. Two distinct $\varepsilon^*$ quantities appear in wrapper analyses … See `#der-class-coercion-via-wrapping` Discussion for the disambiguation."*

## 3.7 Prior art: AAT did not invent wrapping

A final honesty marker before moving on. The wrapping move itself is not original to AAT. AAT's own related-work analysis is explicit[^prior-art]:

- **POMDP belief-state filters** (Astrom 1965; Kaelbling, Littman, Cassandra 1998) are goal-blind by construction. They are the closest formal antecedent to the W₁ structural-separation guarantee.
- **Cognitive architectures** (Newell 1990; Laird 2012; Anderson 2007; CLARION; Global Workspace) have done modular agent design with separated belief / goal / action state for four decades.
- **Tool-using language-model agent frameworks** (ReAct, Reflexion, Generative Agents, MemGPT, Toolformer) are empirical instantiations — most fall in the W₂ behavioral regime; Generative Agents' observation→memory step is the closest empirical instance of W₁.

AAT's contribution is *not* the wrapping move. AAT's contribution is:

1. The *structural-leakage analysis* — the (C1)–(C3) conditions, Theorem 2's KL-leakage form, the $\kappa \le I(A(q_M); G_W \mid q_M)$ structural bound.
2. The *regime hierarchy* — the W₀ / W₂ / W₁ partition that distinguishes structural from behavioral separation guarantees.
3. The *Pearl-blanket-form architectural classification* (Class 1 / 2 / 3) with explicit Class 3 scope honesty, distinguishing the technical conditional-independence statement from contested metaphysical readings of the Markov blanket apparatus.

The reason to be explicit about this is that the convergence argument in §5 is not *"AAT and engineering both discovered this."* It is *"AAT and engineering both reach for something long known in adjacent literatures, and the fact that two distant disciplines independently reach for it is itself evidence about the structural shape of the problem."* Pretending AAT invented wrapping would weaken the argument by making the prior art look like AAT's primary contribution.[^honesty-strengthens]

[^prior-art]: `der-class-coercion-via-wrapping.md` §"Novelty Claim": *"*Claim integration* of POMDP / cognitive-architecture prior art with the AAT Class 1/2/3 (Separated/Partial/Coupled) directed-separation taxonomy, plus the W₀/W₂/W₁ regime hierarchy that surfaces the structural-vs-behavioral leakage distinction and the LLM-specific (C1)–(C3) admissibility/leakage conditions. The wrapping move itself is rediscovery of patterns established in POMDP theory (Bayesian belief-update is goal-blind by construction) and cognitive architectures (modular agent design with separated belief/goal/action state, four decades). AAT's contribution is the structural-leakage analysis at the directed-separation level and the regime hierarchy that names where the separation guarantee lives."*

[^honesty-strengthens]: This kind of prior-art honesty strengthens rather than weakens the eventual convergence claim. If AAT's contribution were the wrapping move itself, the convergence with engineering would be circular — the same idea reaching the same place. Because AAT's contribution is the *analysis layer* (structural-leakage bounds, regime hierarchy, conditions on the component), the convergence is between (a) AAT's analytical work on a previously-known move and (b) engineering's practical convergence on the same previously-known move. Both arrive there independently for structural reasons; the convergence is meaningful precisely because neither side originated the move.

---

*End §3 draft. Word count: ~2,400. To iterate.*
