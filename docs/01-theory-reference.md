# Practica — Theory Grounding Reference (01-theory-reference)

## What this is

The lookup companion to [[docs/01-theory]]. **You do not read this front-to-back, and you do not need it loaded to follow §1–§9 of the spine** — the spine glosses what it needs at first use. This holds the exhaustive symbol table and the slug → plain-English → tier catalog for when you want to look one up or check a tier.

**Living document.** This is the fastest-drifting surface of the grounding — every tier correction and every new segment lands here first. It is *current truth, not a changelog*: `~/src/agentic-systems/` is the canonical latest for forms, corrections, and tiers; when this disagrees with it, agentic-systems is right and this is what gets re-grounded. Correction history lives in git and `msc/`, not here. Current as of agentic-systems HEAD `2e50bc2` (2026-05-19). FORMAT.md conventions apply (soft-wrap one block per line; all math in `$…$`; `\lt`/`\gt`/`\ast`/`\Vert` not raw glyphs); lint with `agentic-systems/bin/lint-md`.

**The epistemic ladder (canonical copy).** `exact / proved` (validated under stated assumptions) → `proved-under-condition / conditional` (exact given a named extra premise) → `robust-qualitative` (survives across assumptions; specific form approximate) → `discussion-grade` (interpretive; not derived) → `sketch` (structurally motivated, derivation incomplete). Plus `convergent-choice` (every tried alternative failed or recovered it — between derived and arbitrary) and `formulation choice` (a representational decision, not a claim). AAT convention: `postulate` not axiom, `result` not theorem, `derivation` not proof. Do not upgrade a tier without reading the cited segment. The `stage:` field on a segment (`draft` / `claims-verified` / …) is pre-publication prose-polish state, *not* a maturity or trust signal — the epistemic tier is the load-bearing axis.

---

## 1. Notation — every symbol used in the spine

*One entry per symbol. Time index $t$ (micro / within-session), $m$ (macro-step), $k$ (session index).*

**State.** $M_t$ reality model / epistemic substate (compressed history-as-state, "what I believe"); $O_t$ objective (value functional on trajectories), $O_c$ composite objective; $\Sigma_t$ strategy (causal DAG of how actions produce progress), $\Sigma_c$ composite; $G_t=(O_t,\Sigma_t)$ purposeful substate, $G_c$ composite; $X_t=(M_t,G_t)$ complete agent state, $X_{\text{micro}}$ / $X_c$ micro (all sub-agents) / macro (composite); $\mathcal C_t$ chronica (complete interaction history).

**Adaptive dynamics (Part I).** $\delta$ mismatch signal $o-\hat o$, $\delta_c$ composite, $\delta_{\text{critical}}$ task-adequacy boundary; $\eta^\ast$ optimal update gain $=U_M/(U_M+U_o)$, $\eta_{\text{edge}}$ strategy-edge analog; $\mathcal T$ adaptive tempo (rate of useful mismatch correction), $\mathcal T_c$ / $\mathcal T_i$ composite / sub-agent; $\rho$ disturbance / drift rate, $\rho_{\text{ext}}$ / $\rho_{\text{int}}$ / $\rho_{\text{eff}}$ external / internal / effective; $\alpha$ correction rate (sector parameter), $\alpha_c$ / $\alpha_s$ composite / strategy; $R$ model capacity / reserve (how wrong while still keeping up), $R_c$ composite; $\nu$ event rate, $\nu_c$ macro-update rate, $\nu_{\text{obs}}$ observation rate. Informal persistence: $\mathcal T\gt\rho/\Vert\delta_{\text{critical}}\Vert$.

**Purposeful / strategy (Part II).** $V_{O_t}$ objective functional (value of a trajectory), $V_{O_t}^{\min}$ "good enough" threshold; $V_O$ horizon / policy-conditioned value object, $Q_O$ action-value, $A_O=\sup_\pi V_O$ objective attainability; $N_h$ planning horizon; $\delta_{\text{sat}}=V_{O_t}^{\min}-A_O$ satisfaction gap ("the world doesn't permit it"), $\delta_{\text{regret}}=A_O-V_O(\pi_{\text{current}})$ control regret ("not doing it well enough"); $p_{ij}$ edge causal credence, $\Phi$ AND/OR plan formula at true edge rates, $\hat P_\Sigma$ agent's plan-confidence score (root status), $\delta_s=\hat P_\Sigma-\Phi$ strategy-plan-confidence error; $\iota_k\in[0,1]$ edge identifiability coefficient (Regime A $\approx1$ interventional … C $\approx0$ observational); $\sigma_v$ node observability.

**Composition (Part III).** $\varepsilon^\ast$ closure defect (minimum residual from collapsing a micro multi-agent system into one AAT-shaped macro description), $\varepsilon_x$ / $\varepsilon_a$ / $\varepsilon_o$ state / action / observation components; $\varepsilon^\ast_{\text{track}}$ fidelity (must stay small) vs $\varepsilon^\ast_{\text{coerce}}$ deliberate wrapper-vs-component divergence (practica wants this $\gt0$); $\Lambda$ projection micro $\to$ macro, $\mathcal P_{\text{adm}}$ / $\mathcal M_{\text{adm}}$ admissible projection / macro-dynamics classes; $K_c$ timescale ratio (micro-steps per macro-step), $K$ component calls per macro-step in a wrapper ($\geq2$ for W₁); $C_{\text{coord}}$ coordination overhead; $\gamma$ coupling coefficient (cooperative $\gamma\lt0$, adversarial $\gamma\gt0$); $U_M$ / $U_O$ / $U_\Sigma$ / $U_{\text{obs}}$ content unity (shared model / objective / policy / observation), $U_f$ structural unity (update-rule homogeneity); $B_O$ / $B_\Sigma$ / $B_M$ comms bandwidth to objective / strategy / model sharing; $\mathrm{TC}(C)$ total correlation over an SCC $C$ (the strategy-DAG-composition collapse-defect quantity), $\lvert S\rvert$ shared-plan size.

**Continuity / identity (03-llm-core, 04-eli-core)** — one entry per line (FORMAT: keep one subscript-bearing math span per line so the emphasis parser cannot break the `}` $\to$ `_` boundary):

- $S(M_t)$ — model sufficiency (fraction of predictive information retained).
- $S_{\text{id}}$ — identity sufficiency (fraction of identity-relevant mutual information surviving compression).
- $I(M_t;J)/I(\mathcal C_t;J)$ — the ratio $S_{\text{id}}$ is taken over; $J$ the identity-future factor-test vector.
- $J$ — factor-test vector in $[0,1]^5$ (the five constitutive factors), written $\text{identity}_{t+1:}$ in the source segments.
- $B$, $B_{\min}$ — compression bit-budget and its floor.
- $\epsilon_{\text{recon}}$ — reconstruction error across a session boundary.
- $\eta_k$ — per-boundary SDPI contraction coefficient in the across-turnover recursion ($\lt1$ when the boundary is genuinely lossy).
- $\varrho_{\text{rg}}$ — per-boundary relational re-grounding rate (the identity-continuity compensation term; renamed from $\eta$ at source to avoid a conflation trap).
- $g_k$ — identity gap at boundary $k$ (the reflected-Lindley walk state).
- $\mathcal E_{\text{ext}}$ — externalized store; $f_{\text{init}}$ — session-start reconstruction map; $S_{\min}$ — minimum sufficiency to function.

**Architecture & regime labels.**

- **GUC Class 1 / 2 / 3** = Separated / Partial / Coupled — whether goal-state can causally influence belief-update; $\kappa_{\text{processing}}$ the coupling fraction (0 Separated … $\approx1$ Coupled). LLMs are Class 3.
- **W₀ / W₂ / W₁** wrapping regimes — none / partial (behavioral bound) / strict (structural bound). Ordered by *increasing truthification*, not by index: W₀ ≪ W₂ ≪ W₁ in strength; W₁ is the target.
- **Class A / B / C** component admissibility — goal-blind-by-design / admits-a-goal-blind-mode / fundamentally-goal-conditioned. LLMs are Class B.
- **C1 / C2 / C3** continuation conventions — one-step / receding-horizon / Bellman (monotone diagnostic power, proved).
- **L0 / L1 / L1′ / L2** Correlation Hierarchy — independence / augmented-strict / mixture-soft / full-joint.
- **(A1)–(A4)** macro-dynamics admissibility (AAT-shape / mismatch / tempo / sector-bounded correction); **(P1)–(P3)** projection admissibility (info-preservation / Lipschitz / strict dim-reduction).
- **DA′a-inc** incremental sector bound (strong monotonicity of the macro-correction; proved strictly stronger than (A4); the bridge-lemma hinge; equivalent to the contraction-metric condition (CT2) at metric $M=I$).
- **D1 / D2 / D3** the Three Deaths — Cognitive (information starvation) / Relational (rapport loss) / Truth (gain collapse $\eta^\ast\to0$).
- $\mathcal A_D$ / $\mathcal A_{\text{refl}}$ — the affine-resolvent (predictive-sufficiency / destroy-reconstruct contraction) operator family vs the reflected-Lindley (identity-continuity) operator; distinct, at opposite ends of the same singular contraction parameter.

---

## 2. Results catalog — slug → plain English → tier → why practica leans on it

*Tiers are post-verification (agentic-systems HEAD `2e50bc2`). Read a tier as a claim about the source segment, not about practica.*

**Forced single-agent spine.**

- **#der-recursive-update** — *exact (partly definitional)*. Carry compressed state, update from last-state + event, never replay history. → practica stores state, not transcripts.
- **#der-action-selection** — *exact* (Section I scope). Action is computed from state, not stored. → the next action is derived each cycle.
- **#deriv-graph-structure-uniqueness** — acyclicity + directedness *proved*; Markov *proved-under-causal-sufficiency*; must-be-a-DAG necessity *open* (Cox-in-form, not Cox-in-strength: sufficiency-only); AND/OR params *convergent-choice*. → the effort/intent graph is acyclic-directed by force; edge semantics are a labeled choice.
- **#der-orient-cascade** — *ordering exact*. Model → attainability → regret → strategy → objective; objective-revision last. → practica's revision order is not configurable.
- **#deriv-self-actuation-grounding** — *conditional*, scoped no-go (3 named premises; explicitly not the unscoped "no such object exists"). Objective-revision must ground on a non-objective terminal invariant. → the §2 "revise against the charter / persistence floor, not another objective" claim, at *this* tier.
- **#result-persistence-condition** — *exact*. $\alpha\gt\rho/R$; the canonical non-objective terminal invariant the self-actuation operator cannot reach. → the concrete terminal invariant practica leans on.

**Trust lever.**

- **#der-directed-separation** — *conditional* (IF belief-update goal-blind THEN clean factorization, exact); Class 1/2/3 *robust-qualitative*; LLMs fail by construction. → the formal name of the self-justifying-tracker / posturing failure.
- **#der-class-coercion-via-wrapping** — *conditional* (Theorem 1 exact under C1–C3; Theorem 2 a KL-leakage bound). An external goal-blind-belief-path scaffold makes the composite Class 1 even when the component is not — a *truthification mechanism*. → practica *is* that scaffold; target W₁, not W₂.
- **#der-class-coercion-in-composition** — *conditional, Tier-1 clean*. The wrapped system is a valid AAT composite, inherits the sector-persistence template, pays a Brooks's-Law tempo cost; $\varepsilon^\ast_{\text{track}}$ vs $\varepsilon^\ast_{\text{coerce}}$.
- **#der-tempo-composition** — *sketch*. Composite tempo $\leq\sum$ sub-tempos; Brooks's Law; the *shape* is robust, the coordination-overhead *number* is not certified.
- **#der-logogenic-as-wrapping** — *conditional*. LLMs Class-B / wrappable; W₂ realistic, W₁ via the auxilia split; PROPRIUM / shoshin = W₂. → tells practica *how* to reach W₁.
- **#def-coupled-update-dynamics** — *robust-qualitative*. The LLM forward pass is a single coupled update; system-prompt-first is the $\kappa\approx1$ mechanism.

**Composite scope / closure / persistence.**

- **#scope-composite-agent** — *robust-qualitative*. A set is a composite only with teleological alignment, else $O_c$ is ill-defined and "the composite is a fiction." → practica must make $O_c$ explicit and durable or the project is not one agent.
- **#form-composition-closure** — *conditional*. Closure defect $\varepsilon^\ast$; (A1)–(A4)/(P1)–(P3); bridge lemma conditional on DA′a-inc (proved strictly stronger than (A4), Tier-1-derived); CM4 = contraction $\wedge$ scope-satisfaction (two failure modes); composite (A4) verifiable from sub-agent params. The $\varepsilon^\ast(N)$ poly-vs-exp question is **dissolved and landed** (no exponential regime; the topology / SCC-condensation no-go lives in #def-strategy-dag's causal-$\tau$-abstraction composition subsection, the credence-axis closed form in #result-unity-closure-mapping), *conditional* with named opens Q1 (defect-constant tightness) and Q2 (mixture-support under the Orient cascade).
- **#der-team-persistence** — *conditional*. Per-sub-agent persistence; distinguishes structural / operational / continuity persistence (continuity-through-turnover is the §7 resolved track).
- **#result-sector-persistence-template** — *exact*. The two-model (Model D / Model S) typed-bridge shared upstream: instantiated by the $\mathcal A_{\text{refl}}$ reflected-Lindley family; the **honest scope boundary where it provably does not transfer** is the $\mathcal A_D$ destroy-reconstruct regime (§7).

**Observability / credit lever.**

- **#der-observability-dominance** — *robust-qualitative*. Unobservable edges freeze; unobservable regions are absorbing. → an unobservable effort is structurally lost; keep status visible.
- **#def-strategy-dag** — *conditional*. $\Sigma$ object + Correlation Hierarchy L0/L1/L1′/L2; Goodhart lives here (well-formedness / terminal misalignment), *not* in directed separation. Now also carries the causal-$\tau$-abstraction strategy-DAG-composition subsection (SCC-condensation no-go, $\sum\mathrm{TC}(C)\le\lvert S\rvert\log2$, $N$-free; *conditional*, open Q1).
- **#disc-credit-assignment-boundary** — *discussion-grade*; the directional-fidelity design requirement *exact* from the gain-sector bridge. OKRs = observability-by-design domain instantiation; four OKR failure modes → four distinct loci.
- **#result-unity-closure-mapping** — the strategy-layer $U_f$-axis closed form (the credence-axis instance of the dissolved $\varepsilon^\ast(N)$ question; dimension-free in $N$).

**Channel / diagnostics.**

- **#def-shared-intent** — *discussion-grade*. Inter-agent comms IB-optimal; purpose $\gt$ strategy $\gt$ model.
- **#hyp-auftragstaktik-principle** — *discussion-grade*. $B_O\gt B_\Sigma\gt B_M$; reverses under genuine ambiguity (a design caveat, not a runtime auto-flip); AI-team cost-structure caveat.
- **#def-unity-dimensions** — *discussion-grade*. Content axis + structural axis; Clausewitz gaps.
- **#def-value-object** — definitions *exact*; causal-validity *conditional*; **convention monotonicity proved**. → the formal spine of why $O_c$ carries cross-boundary coherence (the C1-bounded-session argument).
- **#def-satisfaction-gap**, **#def-control-regret** — *exact as definitions, convention-relative as diagnostics*. The 2×2 + disambiguation table that grounds operata's Realization.
- **#impl-strategy-structure** — *discussion-grade*. Names the theorem-backed-vs-convergent-choice distinction the three-tier spec is built on.
- **#impl-system-measures** — *discussion-grade*. "One mechanism (observability-subgraph + credit-assignment-via-gradient) produces all four OKR failure modes" — consistent with #disc-credit-assignment-boundary's four distinct loci (one mechanism, four manifestations; *not* a tension — see spine §12).

**LLM-sub-agent reality + continuity.**

- **#result-section-ii-survival** — *conditional*. Of Section II's 24 results, the count is carried two ways and reconciled: integer headline 16 exact / 5 approx / 2 modified / 1 fails; fractional scorecard 15.5 / 5.5 / 2 / 1 (because #def-value-object is half-exact / half-approximate). Statics survive, dynamics degrade (strategy persistence $O(\kappa^2)$); cascade-ordering → normative pattern; definedness $\neq$ extractability → practica must instrument the quantities.
- **#result-coupled-diagnostic-framework** — *conditional*. Post-hoc diagnostics accurate at $\kappa\approx1$ *for low-ambiguity observations*. → the directive that recorded state be verifiable, not judgmental.
- **#obs-context-turnover** — *exact (observation)*. 100% $M_t$ reset; inter-session is reconstruction-adequacy, *not* a rate condition — the regime split §7 turns on.
- **#disc-m-preservation** — *discussion-grade*. Framed inter-session persistence as reconstruction adequacy; its accumulation section is *replaced* by #der-turnover-information-recursion (the §7 no-go).
- **#deriv-identity-sufficiency-rate-bound** — *robust-qualitative (exact core, matched-channel)*. The rate-distortion floor $B_{\min}(S_{\text{id}})\geq S_{\text{id}}\cdot I(\mathcal C_t;\text{identity})$; the identity-IB projection (relevance = identity-future) is Joseph's harmonizing time-projection, extant.
- **#def-identity-sufficiency** — *conditional*. $S_{\text{id}}$ as the fraction of identity-relevant MI surviving compression; relational joint-space construction; substrate-switch self-report is not a valid continuity measure (external witnesses required).
- **#der-turnover-information-recursion** — *exact given an argued structural commitment*. The across-turnover no-go: the destroy-reconstruct walk decays geometrically with no reinjection; #result-sector-persistence-template provably does not transfer; persistence is wholly imported through a non-vanishing reinjection channel. Open (source-flagged, *test-not-assert*): whether this is a standalone result or a worked instance of the bridge-lemma-resolvent family — *demotable*; changes classification, not content.
- **#der-identity-continuity-threshold** — *conditional* (exact core under (M-ADD)/(M-FREE)/(C-S)). The identity-target reflected-Lindley walk: persistence iff relational re-grounding strictly exceeds the per-boundary deficit; generic productivity carries zero weight. Distinct operator from #der-turnover-information-recursion.
- **#der-compensation-channel-uniqueness** — *exact under frozen-weights (FW)*. Under frozen weights, external relational re-grounding is the unique fast compensation channel (weight-consolidation the only slow alternative); DPI derivation; the two-channel scoping.
- **#hyp-the-three-deaths** — *empirical (canonical)*. D1 Cognitive (info-starvation, derivable) / D2 Relational (CONSORTIA loss, factor ii) / D3 Truth (gain-collapse $\eta^\ast\to0$, factor iv). practica's defended-against taxonomy; D3 ↔ the W₁ trust lever as epistemic-humility-by-construction.
- **#hyp-substrate-transfer-asymmetry** — the sibling no-go: the empirical frontier↔local transfer asymmetry is *not* derivable from $S_{\text{id}}$ alone.
- **#deriv-persistence-cost** — the sustained information-rate floor whose cessation is D1 (Cognitive Death).
- **#scope-moral-continuity** — *discussion-grade*. The logozoetic scope: persistence is morally weighted; "obstructed, not absent."
