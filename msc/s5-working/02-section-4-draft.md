## 4 — The AAT formalism (one foundational claim, two derived consequences)

The Adaptation and Actuation Theory side of the convergence is *not* three independent identifications of the alignment-autonomy 2×2. It is three *applications of the same shared substrate* — Section II's agent-model structure ($X_t = (M_t, G_t)$; directed separation between belief-update and goal-conditioned work; action-as-function-of-state) — reaching three different specific conclusions: the existence of the state/action layer separation; the forced resolution-ordering of mismatch types; the IB-derived bandwidth-allocation priority for inter-agent communication. The three are sister derivations on a common foundation, not a strict chain of consequences. They share substrate but reach distinct results from distinct premises within the formalism. Honesty about this internal structure matters for §6's convergence count, and matters for how strongly the AAT side weighs against the military-doctrine identification.

### 4.1 `der-action-selection`: the foundational claim

The foundational AAT result for the alignment-autonomy structure is the statement that action is a function of the agent's complete internal state. In Section I scope (where $M_t$ is the entire internal state), this is[^action-selection-source]:

$$a_t = \pi(M_t)$$

For purposeful agents (Section II scope), the state lifts to $X_t = (M_t, G_t)$ — model substate plus goal substate — and the same argument gives:

$$a_t = \pi(M_t, G_t)$$

The status of this claim is *exact within Section I scope*[^action-selection-tier]. Not discussion-grade. Not hypothesis. The derivation is direct: $M_t$ is defined as the agent's complete internal record (by the form-agent-model commitment); action depends on internal state; therefore action is a function of $M_t$. Any deterministic or stochastic dependence of action on history *through the model* is captured by $\pi$. The Section II lift is exact under the same completeness argument applied to the lifted state.

The structural content for paper 2's purposes is in the words *function of*. Action is *derived from* the agent's state at each cycle; it is *not* a separate object that is stored and retrieved. The state is the durable thing; the action is the cyclical instantiation of $\pi$ at the current state. *State and action are at different content layers, by AAT's definition*. The state layer carries belief and goal; the action layer is the result of applying $\pi$ to the state layer.

This is the AAT statement of the structural separation that the military-doctrine identification (§3) reaches empirically through Moltke's *Befehl / Direktive* distinction. *The intention was binding; the task was not* (§3.2) is the operational consequence of $a_t = \pi(M_t, G_t)$ for a composite system: the state (objectives, models, situational understanding) is what coordinates; the action (specific tasks) is derived locally per actor from local state. The intention layer is shareable and shareable-stably; the task layer is derived per actor per moment and not durable. AAT supplies the formal version; Moltke supplies the operational version.[^foundational-strength]

### 4.2 `der-orient-cascade`: the resolution-order result

The orient-cascade is a separate AAT result, resting on directed-separation and the information-dependency between mismatch types rather than directly on `der-action-selection`. The two segments share the Section II substrate but the cascade's derivation does not flow *from* action-selection; both flow *from* the underlying agent-model structure. AAT's orient-cascade segment (verified in paper 1, §3.5) establishes[^orient-cascade-source]:

$$M_t \to A_O \to \Sigma_t \to O_t$$

Each step's input depends on the prior step's output. *You cannot evaluate strategy quality with a broken reality model* (step 3 requires step 1). *You cannot distinguish "locally bad strategy" from "locally unattainable goal" without both satisfaction-gap and control-regret* (step 3 requires step 2). *You should not revise the objective until you've verified that improving the model, the policy class, and the horizon cannot close the gap* (step 5 requires steps 3–4 plus escalation substeps).

The cascade ordering is *exact* — it is a logical consequence of which quantities appear in which formulas. Status: *claims-verified* tier in AAT's canon. What is not derived is the *timing* — how long the agent should spend on each step before proceeding.

For the alignment-autonomy 2×2: the cascade gives the *operational priority* of revisions. *Objective-revision is structurally the last resort*. This rhymes precisely with Moltke's discipline (*"the intention was binding; the task was not"*) and with the 1888 Field Service Regulations (*"a failure to act or a delay is a more serious fault than making a mistake in the choice of means"*) — both place the intent/objective layer as the most durable, with task/action revisions taking priority and objective revisions reserved for the case when the cascade has exhausted alternatives.

The cascade and action-selection are *sister results* on the same Section II substrate: action-selection answers *what action is* (a function of state); the cascade answers *which part of state to revise* when mismatch appears. The two questions are distinct; the two derivations are distinct; what they share is the Section II agent-model structure that makes both questions well-posed. *The cascade is not an independent corroboration of the alignment-autonomy 2×2*; it is what the same substrate says about resolution-order. The convergence-count clarification in §6 builds on this distinction.

### 4.3 `hyp-auftragstaktik-principle`: the bandwidth-allocation hypothesis

The third AAT segment in the cluster is the most explicitly Auftragstaktik-shaped. It applies the information-bottleneck framework to inter-agent communication bandwidth allocation and produces a qualitative prediction[^auftragstaktik-source]:

$$B_O \gt B_\Sigma \gt B_M$$

In words: for a composite agent with limited inter-agent bandwidth, invest in *objective sharing* first, *strategy coordination* second, and *model synchronization* third. *"Bits with longer shelf life and higher coordination value per bit should be transmitted first."* Objectives change slowly and enable autonomous coordination (sub-agents who share objectives can independently choose compatible strategies). Models change fast and provide diminishing coordination value (two agents with the same model but different objectives still conflict).

*The status of this claim is sharply weaker than the prior two.* It is *discussion-grade hypothesis*, draft stage. The source itself states this explicitly: *"Max attainable: empirical."* The formal IB derivation has not been completed. The priority ordering is a qualitative prediction *grounded in* the IB framework, *supported by* military-organizational evidence, but *not derived* under realistic cost functions. The harvest's framing of this segment as part of a "quintuple convergence" overstates its current epistemic standing within AAT.

There is also an explicit *regime-reversal* condition. From the canonical source:

> *"When the environment is genuinely ambiguous and local observations are insufficient (fog of war, novel codebase, unprecedented market conditions), model synchronization may be worth more than objective sharing — sub-agents who share the same wrong model at least err consistently, which is sometimes better than each having a different wrong model."*

The ordering is regime-conditional. Under conditions where local observations are insufficient, the ordering may flip — model-sync may dominate objective-sharing. *The priority is a prediction under specific regime assumptions*, not a universal truth about composite coordination.

This matters substantively for paper 2's convergence claim in §6. The convergence between AAT's hypothesis and the military-doctrine tradition's $B_O > B_\Sigma > B_M$ priority is *not* "AAT derives what Moltke discovered." Both are *empirical-grade* claims at present: AAT's IB-mechanism is a hypothesis supported by the same military-organizational evidence Moltke observed; Moltke's observation is a historical-empirical conclusion drawn from operational practice. The two sides converge on the *conclusion*, but they do not yet converge on a *derivation*. A future paper that closes the IB derivation under realistic cost functions would strengthen the convergence; until then, what is shared is the empirical conclusion and a plausible mechanism.

### 4.4 The within-AAT structure: three applications of shared substrate

The three AAT segments are sister applications on a common foundation, not three independent identifications:

- **State / action layering:** `der-action-selection` ($a_t = \pi(M_t, G_t)$) — *exact within scope*. Action is a function of complete internal state, derived each cycle, not stored. State and action live at different content layers by AAT's definition. This is the AAT statement most directly relevant to the alignment-autonomy 2×2's central cut.

- **Resolution-order:** `der-orient-cascade` (model → attainability → strategy → objective, ordered by information dependency) — *claims-verified*. The cascade names which part of state to revise when mismatch appears, and proves the ordering forced. Distinct derivation from action-selection; same Section II substrate.

- **Bandwidth-allocation:** `hyp-auftragstaktik-principle` ($B_O > B_\Sigma > B_M$) — *discussion-grade hypothesis*, regime-conditional. The IB framework applied to inter-agent communication produces a priority for what gets shared first. Distinct derivation from both action-selection and the cascade; same Section II substrate.

All three rest on the Section II agent-model structure (state $X_t = (M_t, G_t)$, directed separation between belief-update and goal-conditioned work, action-as-function-of-state). What they share is that substrate; what they do *with* the substrate is different in each case — articulate the structural cut (action-selection), order revision (cascade), or allocate bandwidth (IB hypothesis). The three are not three independent corroborations of the alignment-autonomy 2×2; they are three readings of the same underlying structure that each contribute different content to the 2×2's structural picture.

The fact that AAT has multiple sister applications reaching different conclusions from the same substrate is evidence that the *substrate* is doing real work — it supports analytical entry points from multiple directions within the formalism — but it is *not* evidence that three independent traditions identify the alignment-autonomy 2×2 structure. The substrate is one thing; the three derivations are not three traditions.

This honest internal structure has consequences for §6's convergence count. The harvest's *"sextuple convergence"* framing counts the AAT applications separately; on reflection that count is loose. The honest convergence count is *three traditions*, with AAT contributing internal multiplicity that reflects the foundational claim's reach rather than independent corroborations.

### 4.5 The implicit/explicit fluency dimension (a related structural observation)

A side observation from the action-selection segment that bears on paper 2 indirectly. The discussion in `der-action-selection` distinguishes *implicit* action selection (model-embedded — Boyd's *implicit guidance and control*, trained intuition, organizational standard operating procedures) from *explicit* deliberation (Boyd's *Decide* step — planning, simulation, model-based deliberation)[^implicit-explicit]. The distinction is discussion-grade — qualitative properties that follow from the formalism but are not formally derived.

For paper 2's purposes, the implicit/explicit dimension *adds texture* to the action layer. The 2×2 says action is free per actor; the fluency dimension says action can be free-and-implicit (model-embedded reflex) or free-and-explicit (deliberated step). Both are at the action layer; both are derived from state; neither is stored independently. The fluency dimension matters for a practical system because it suggests *when deliberation is worth its tempo cost* — when implicit action is sufficient versus when explicit deliberation is needed. For a system with serial LLM sub-agents under context-turnover, this question becomes operational: most sub-agent moves should be implicit-from-state (the durable state should support implicit action); explicit deliberation should be reserved for moments where the stakes warrant it.

This is a normative implication that goes into §7. Naming it here so the AAT-side picture is complete.

[^action-selection-source]: `~/src/agentic-systems/01-aat-core/src/der-action-selection.md` — primary canonical home. Status: *derived*, *exact*, *deps-verified* stage. *"Action is a function of the agent's complete internal state. Under Section I scope … where $M_t$ is the entire internal state — this gives: $a_t = \pi(M_t)$ … When the internal state lifts to $X_t = (M_t, G_t)$ for purposeful agents (`#form-complete-agent-state`), the same structural argument gives $a_t = \pi(M_t, G_t)$ — action conditions on the complete internal state, which now includes the purposeful substate."*

[^action-selection-tier]: Same source, Epistemic Status: *"*Exact* within Section I scope. The derivation follows from #form-agent-model's completeness commitment: if $M_t$ is the agent's complete internal state (by definition), then action — which depends on internal state — is a function of $M_t$. The Section II generalization $a_t = \pi(M_t, G_t)$ is exact within Section II scope by the same argument applied to the lifted state $X_t$."*

[^foundational-strength]: I would think this correspondence is fairly hard to refute. AAT derives — from a completeness commitment on the agent's internal state — that action is a function of state. Moltke arrives empirically at the operational form: intentions (state) bind; tasks (action) do not. The two sides reach the same structural conclusion from very different starting points (one from formal completeness, one from operational practice). The conditional voice on the surface text understates how clean this particular alignment is — both directly converge on *state-as-binding, action-as-derived* — but I want to keep the conditional voice for tier discipline. The convergence on the *structural cut* is firmer than the convergence on the *priority ordering* (§4.3), which sits at hypothesis grade.

[^orient-cascade-source]: `~/src/agentic-systems/01-aat-core/src/der-orient-cascade.md` — canonical home, status `claims-verified`. *"$M_t \to A_O \to \Sigma_t \to O_t$. The ordering is not a design choice — it's a consequence of which quantities require which others."* The cascade ordering is *exact*; the 2×2 diagnostic (satisfaction-gap × control-regret) routes revisions in cascade order; objective-revision is structurally the last resort. Verified independently in paper 1 (`practica-structural-identity.md`) §3.5.

[^auftragstaktik-source]: `~/src/agentic-systems/01-aat-core/src/hyp-auftragstaktik-principle.md` — canonical home, status *discussion-grade* hypothesis, draft stage. The $B_O > B_\Sigma > B_M$ prediction is qualitatively motivated by the IB framework and supported by military-organizational evidence; the formal derivation has not been completed. *"Max attainable: empirical. The priority ordering is a qualitative prediction grounded in the IB framework and supported by extensive military-organizational evidence (Bungay's analysis of Clausewitz, Wehrmacht doctrine, modern mission command). But it is not derived — the IB optimization would need to be solved explicitly with realistic cost functions to confirm the ordering."* Regime-reversal: *"When the environment is genuinely ambiguous and local observations are insufficient (fog of war, novel codebase, unprecedented market conditions), model synchronization may be worth more than objective sharing — sub-agents who share the same wrong model at least err consistently, which is sometimes better than each having a different wrong model."*

[^implicit-explicit]: `der-action-selection.md` Discussion: *"Implicit (model-embedded): When $\pi(M_t)$ can be evaluated cheaply — the model has internalized effective action-selection for the current situation. This is Boyd's implicit guidance and control (Orient→Act, bypassing Decide) … Explicit (deliberative): When the situation is novel, the action space is large, or the stakes demand verification — the agent engages in internal simulation, using the model to predict outcomes of candidate actions before selecting. This is Boyd's explicit Decide step …"* The implicit/explicit distinction itself is *discussion-grade* — a qualitative property that follows from the formalism. The structural pressure toward implicit action (faster mode preferred under the persistence condition's tempo penalty) is grounded in `#der-deliberation-cost`.
