# Practica's structural identity — comparative descriptive paper (s4 working)

**Working substrate.** Iteration channel for the paper. History → git; conclusions → the eventual paper at `docs/` (location TBD). Premise + outline + source-checklist + open questions, updated as iteration proceeds. Not a durable artifact; can stay verbose and process-shaped.

## Premise (first-pass, conditional)

**Convergence claim under examination.** The structural job a system like practica must perform — for a composite of serial sub-agents under context-turnover, whose components are Class 3 substrates (e.g. LLMs) — has been independently identified across three distinct origins. The identifications use different vocabularies but pick out the same structural shape:

- **AAT's wrapping construction (M1):** wrapping a Class 3 component produces a Class 1 composite *at the wrapper level by construction*, at measurable cost (tempo overhead; residual leakage).
- **AAT's external cascade-recovery (O2):** scaffolded loops reproduce the orient-cascade ($M_t \to A_O \to \Sigma \to O$) externally, for substrates that cannot produce the resolution-ordering internally because it lives in one merged forward pass.
- **Operata's plumbing / intelligence split (E6):** an abandoned-Dec-2025 engineering precedent that reached a ~60% deterministic / 40% intelligence split *before* the AAT formalism existed.

**Supersession claim under examination.** *If* the structural identification holds, several operational design constraints — bootstrap-recovery-safety (E1), soft-claiming over locking (E2), day-one DAG-with-cycle-detection (E5) — follow as *consequences* rather than as independent design choices.

Both claims are stated *conditionally*. Current backing: AAT side at **discussion-grade synthesis tier** (home segments verify the formal claims at higher tier individually, but the synthesis is hub-level); operata side as **engineering precedent** — *"convicted of the shape,"* not *"validated by production."* The convergence pattern itself is the substantive result this paper is comparing. The supersession is a candidate entailment to be examined, not derived.

## Audience and voice

- **Audience.** Highly-literate but general peers who know practica's stated goal (the hierarchical and meaningful graph of ongoing efforts) and have *mild* AAT familiarity but no formal AAT grounding.
- **Voice.** Calibrated humility per the harvest discipline. Tier marks. Bridge-uncertainty explicit. Strong-where-warranted; conditional where the bridge is mine. If on reflection a conclusion is stronger than the surface text shows, the strength-flag goes in a footnote per Joseph's instruction — *e.g.* `[^n]: I would think this is very hard to refute. I've tried.`
- **Citations.** Markdown footnotes. Footnote body = local file link **+** supporting quote or math. Self-supporting for a reader who wants to verify any specific claim without trusting me.

## Rough outline (placeholder — refine after source reads)

1. **Introduction.** Practica's stated goal. The question this paper takes up: what structural job must a system like practica do, for a composite of serial sub-agents whose components are Class 3 substrates under context-turnover? Why convergence-across-traditions is the right frame for thinking about a system's structural identity.

2. **The problem the structural job solves.** Composite truth-tracking when components are Class 3 substrates. Brief introduction to Class 1/2/3 (just enough for the audience — the substrate-categorical distinction, not the full machinery).

3. **First locus: AAT's wrapping construction (M1).** Formal derivation in canon. The two closure-defect quantities $\varepsilon^*_{\text{track}}$ and $\varepsilon^*_{\text{coerce}}$ from FCC1 sharpen what wrapping actually does — distinguishing leakage-as-error from coercion-as-value.

4. **Second locus: AAT's external cascade-recovery (O2).** The orient-cascade cannot be produced internally by a substrate whose resolution lives in one merged forward pass. Scaffolded loops reproduce it externally.

5. **Third locus: operata's plumbing / intelligence split (E6).** Engineering precedent. ~60/40 reached pre-theory; F5 in operata's own TODO names the principle. 30/30 BDD-green at abandonment is the empirical texture — *engineering didn't ship but the shape held*.

6. **The convergence.** Three vocabularies, same structural shape. The plumbing IS the wrapping IS the external cascade-recovery. Convergence-across-distinct-origins is itself the substantive result; the structure appears *forced by the problem* rather than chosen by any one tradition.

7. **Supersession structure (conditional).** If the identification holds, the engineering consequences (E1/E2/E5) follow. Each consequence traced to which part of the structural identification forces it.

8. **Honest limits.** What this paper does NOT establish. AAT discussion-grade synthesis vs. theorem-grade home segments. Operata as precedent-without-production-validation. The conditional nature of the supersession structure.

9. **Conclusion.** What the convergence is and isn't.

## Source-verification checklist (read-before-promote)

The harvest cites discussion-grade synthesis hubs. Before any specific quote or math enters the paper, the **home segment** must be read and the quotation/inequality verified against the canonical source.

**AAT canon — required reads:**
- [ ] `~/src/agentic-systems/01-aat-core/src/der-class-coercion-via-wrapping.md` (M1 primary home)
- [ ] `~/src/agentic-systems/01-aat-core/src/der-class-coercion-in-composition.md` (M1 supporting)
- [ ] `~/src/agentic-systems/01-aat-core/src/form-composition-closure.md` (FCC1 — $\varepsilon^*_{\text{track}}$ vs. $\varepsilon^*_{\text{coerce}}$ formal definitions; CM4 conditions)
- [ ] `~/src/agentic-systems/01-aat-core/src/der-orient-cascade.md` (O2 primary home)
- [ ] `~/src/agentic-systems/01-aat-core/src/der-directed-separation.md` (Class 1/2/3 architectural distinction; substrate scope)

**Operata — required reads:**
- [ ] `~/src/operata/TODO.md` (F1–F5 lived-experience entries; F5 is the plumbing/intelligence split)
- [ ] `~/src/operata/docs/glossary.md` (terminology precision)
- [ ] `~/src/operata/docs/sys/` (system overview; resource specs)
- [ ] `~/src/operata/docs/exp/2025-11-14-operata-principles.md` (productive tensions; principle-naming)

**Source 3 (Bungay), selective:**
- [ ] `~/src/_ref/books/Art-of-Action/Art-of-Action.md` Ch 7 specifically — the executive trinity (*directing / managing / leading*) — for the open question of whether this is a *fourth locus* or comparative reference.
- [ ] `msc/s3-working/03-the-solution.md` and `05-strategy.md` for the per-chapter wandering on wrapping-shaped claims (Auftragstaktik as form-content separation).

**Emerson (only if used):**
- [ ] `ref/tas.md` — Pestalozzi quote on *"help must come from the bosom alone"* — probably background context for the agency-grant framing, not load-bearing for the convergence claim itself.

## Open questions to resolve before first draft

1. **Bungay as fourth locus or comparative reference.** The executive trinity (directing/managing/leading) potentially maps onto plumbing/intelligence/(human-only) — but the mapping is not obviously clean. Ch 7 reading needed before deciding. *Disposition for now:* treat as comparative reference; a triple-locus paper is honest, a stretched quadruple would dilute. Will reconsider after Ch 7.

2. **Depth of AAT-formalism introduction.** Mild AAT familiarity → introduce $W_0/W_1/W_2$, Class 1/3, the wrapping construction, the orient-cascade — but do not *derive* any of them. Heuristic: every introduced concept must be load-bearing for the convergence claim, not present because it's *"AAT background."*

3. **Math density.** Definitions and key inequalities (closure-defect quantities; orient-cascade ordering) in display form with full citation. Derivations described qualitatively with pointers to home segments. Test by drafting Section 3 and asking: does the math help land the claim, or is it ornament?

4. **Framing the convergence: research-result vs. scaffolding-for-supersession.** Two valences possible. (a) *"the convergence is itself the substantive result of this paper"* — honest at current tier. (b) *"the convergence justifies treating the structural identity as forced, which licenses the supersession structure"* — what a stronger paper *could* claim if home segments fully verify. *Disposition for now:* (a), with (b) gestured at in the conclusion as the natural next move once verification is complete.

5. **Conditional-voice load.** Every *"this implies" / "follows from" / "is forced by"* in the supersession section needs an explicit hedge. Draft Section 7 first to check whether the hedge load is manageable or whether the prose drowns in conditionals. If drowning: redesign the section (footnote-cluster the conditionals; reserve plain prose for the structural claim).

## Process

- **This iteration:** the working file (you are reading it).
- **Next:** read AAT home segments + operata sources; update working notes with *verified vs. unverified* claim status. Update outline if sources change the shape. Read Ch 7 (Bungay) to resolve open question 1.
- **Then:** first prose draft of one section — probably Section 3 (AAT wrapping construction), since it has the most formal content to get right, and its tone sets the precedent for the rest.
- **Then:** remaining sections, one or two per iteration.
- **At or after first complete draft:** adversarial pass per Joseph's instruction — *overclaim, underclaim, ungrounded, assumed*. Then Truth/Honesty judgment pass. Then commit.

## Failure modes to watch

- **Voice:** borrowing AAT's theorem-grade authority for synthesis-grade claims. *Guard:* any *"wrapping produces…"* statement carries the home-segment tier in prose or footnote.
- **Supersession:** stating *"follows from"* in a way that hides *"follows from* if *the synthesis-grade identification holds."* *Guard:* conditional voice on every supersession claim.
- **Audience:** assuming AAT vocabulary the reader doesn't have. *Guard:* every term introduced traceable to first use.
- **Pedagogical inflation:** the paper becoming an AAT introduction with the convergence claim tacked on. *Guard:* every concept introduced must be load-bearing.
- **Convergence stretch:** reaching for a fourth locus to make the convergence count higher. *Guard:* triple is honest; quadruple only if the Bungay Ch 7 mapping holds up under careful read.

---

## Verification log — round 1 (after AAT source reads + operata partial)

### What verified solidly

- **The wrapping construction (M1).** `der-class-coercion-via-wrapping.md` derives directed separation at the wrapper level under (C1)–(C3) admissibility on the component. Two formal theorems: Theorem 1 (exact form under strict (C3)) and Theorem 2 (approximate form with KL-leakage bound $\kappa$). The W₀/W₂/W₁ regime hierarchy is *more nuanced* than the harvest summary: **W₀** = unwrapped (raw Class 3); **W₂** = partial wrapping (one goal-conditioned call per macro-step, response parsed) — bounded *behaviorally* by the component's instruction-following; **W₁** = strict wrapping (separate goal-blind $q_M$ and goal-conditioned $q_G$ calls) — bounded *structurally* by mutual information $I(A(q_M); G_W \mid q_M)$ in the pretraining distribution. Truthification is the *direction* W₀ → toward W₁; the harvest's "$W_0 \to W_1$" framing is essentially right but should be more careful about W₂ as the intermediate behavioral regime.

- **The wrapper is a valid AAT composite agent (composition-level consequences).** `der-class-coercion-in-composition.md` derives this under wrapper-design constraints (D-A2)–(D-A4). Inherits sector-persistence template at the wrapper level. Pays a tempo cost in the Brooks's-Law form: $\mathcal T_W \leq \mathcal T_A^\text{nominal} - C_\text{coord}^\text{wrap}$.

- **The two closure-defect quantities ($\varepsilon^*_{\text{track}}$ vs. $\varepsilon^*_{\text{coerce}}$).** Distinguished explicitly in *both* `der-class-coercion-in-composition.md` (Discussion §"Coercion-distance vs. tracking-distance") and `form-composition-closure.md` (Discussion §"Constructive (A1)–(A4) via wrapping"). $\varepsilon^*_{\text{track}}$ = fidelity (bounded by bridge lemma); $\varepsilon^*_{\text{coerce}}$ = wrapper-vs-component behavioral divergence (NOT bounded by bridge lemma; it is the *wanted* deviation that *makes* the truthification work). The source explicitly warns: *"Conflating them propagates downstream confusion."*

- **Wrapping as truthification mechanism — named in canon.** `der-class-coercion-via-wrapping.md` Discussion §"Wrapping as a truthification mechanism" explicitly names this and calls the wrapping construction the "rigorous formal version" of defensive scaffolding from `#disc-adversarial-coupling-pressure` (peer review, prediction registers, double-entry bookkeeping). This validates the harvest's M1 framing.

- **The orient-cascade ordering is exact.** `der-orient-cascade.md` status: `claims-verified` — higher tier than the harvest implied. The cascade *ordering* is exact (forced by information dependency); the cascade *content* for steps 3-5 has progressed but specific implementations remain engineering. The 2×2 diagnostic (satisfaction-gap × control-regret) is convention-indexed (C1/C2/C3 monotonicity).

- **Class 3 substrates can't produce the cascade internally — but the wrapping makes them able to.** `der-directed-separation.md` explicitly: *"Class 3 (Coupled) components can be wrapped into Class-1 composites via the construction of `#der-class-coercion-via-wrapping`."* Cascade applies to the wrapper.

- **Operata named the plumbing/intelligence split.** `2025-11-26-operata-system.md` §"LLM agent patterns reveal the plumbing/intelligence split" and Conclusion: *"This separates 'what to do' (agent intelligence) from 'when to do it' (CLI/scheduler determinism)"* — *"deterministic state management beneath the intelligence layer."* The principle is named explicitly.

- **The bootstrap-recovery principle (E1).** Verified by operata's own TODO.md §"Why not dogfood operata with operata yet?" — *"If a bug in operata prevents you from reading your task list, you can't see what to fix. Need a stable/unstable separation."* Engineering-grounded in operata's own voice.

- **Soft-claiming over locking (E2).** Verified — operata glossary names it: *"Status-based signal that an agent is working on something without hard locking."* Operata-system doc describes the pattern in detail.

- **F1 LOCUS-vs-Personal split, F2 intent-vs-action tension, F3 tree-vs-DAG, F4 lost-state.** All four operata-study F-numbers verified verbatim against operata's own TODO.md sections.

### What shifted from harvest framing — important reshape

**The convergence is *not* "three independent loci" (M1 + O2 + E6).** Two important nuances surfaced from the source reads:

1. **M1 and O2 are not fully independent within AAT.** They are *two readings of the same wrapping construction*, emphasizing different functions. M1 reads the construction as *truthification* (W₀ → W₁ direction; structural separation by query type signature). O2 reads it as *cascade-recovery* (once Class 1 is achieved at the wrapper level, the orient cascade applies — recovering external what the Class 3 substrate can't produce internally). Both flow from `der-class-coercion-via-wrapping` + `der-directed-separation`. The *fact that the same construction performs both functions* is itself notable — but it does not constitute two independent loci.

2. **The engineering side is broader than just operata.** Operata's `2025-11-26-operata-system.md` arrives at the plumbing/intelligence split *by observing LLM-agent engineering patterns* — explicitly Claude Code's TodoWrite/TodoRead and LLMCompiler's DAG-with-scheduler pattern. So the convergence is between the AAT formal apparatus and a *family of engineering patterns* in which operata is the explicit-naming instance, while TodoWrite and LLMCompiler are *enacted* instances arrived at independently. This is a stronger story than the original, not weaker.

**Revised convergence framing.** The paper claim should be:

> The same structural identification — that a system using a Class 3 (Coupled) substrate must externalize the cascade-ordering and the goal-blind belief-update by structural commitment, paying a measurable cost in tempo overhead and residual leakage — has been arrived at independently by:
>
> (a) AAT's formal apparatus, in the form of the wrapping construction and its composition-level consequences;
>
> (b) the LLM-agent engineering community, in the form of plumbing/intelligence-split patterns (TodoWrite, LLMCompiler) that working systems have converged on without theoretical scaffolding;
>
> (c) operata's explicit naming of the principle from observing (b), reaching the architectural commitment before AAT existed but without the formal-leakage analysis AAT supplies.
>
> The convergence is between a *formalism* and a *family of engineering practices*, with operata as the bridge — engineering-naming the principle that AAT formally derives.

**Honesty markers I must carry:**

- *AAT's contribution is not the wrapping move itself* — that's POMDP / cognitive-architectures rediscovery (40+ years of prior art, explicitly acknowledged in `der-class-coercion-via-wrapping` Novelty Claim). AAT contributes the **structural-leakage analysis** and the **regime hierarchy** (W₀/W₂/W₁).
- *Operata did not invent the plumbing/intelligence split* — it named the principle from observation of LLM-agent patterns. The convergence story is *broader*, not "operata invented it independently."
- *The "60/40 deterministic/intelligence" percentage* from the harvest's E6 is **NOT** verified by the operata source I read. The principle is named; the percentage is not. **Drop the percentage from the paper unless I find it in a later source read.**

### Supersession structure — verification

The engineering consequences holding up under verification:

- **E1 (bootstrap-recovery):** verified verbatim from operata's own *"Why not dogfood…"* note. Operata died of failing this. Follows from the structural identification because the plumbing layer must be inspectable / restorable when the intelligence layer is unavailable.

- **E2 (soft-claiming over locking):** verified — operata's glossary and the operata-system doc both name it. Follows because serial sub-agents under context-turnover can't hold locks across the boundary.

- **E5 (day-one DAG-with-cycle-detection):** verified — operata's TODO §"Intent Graph: Tree → DAG Migration" explicitly says they knew on day one but shipped a tree and were abandoned mid-migration. Follows because the plumbing layer must enforce structural invariants the intelligence layer cannot self-enforce.

The supersession structure I sketched holds. Conditional voice on each.

### Still pending

- [ ] `~/src/operata/docs/exp/2025-11-14-operata-principles.md` — for E8 productive tensions, and any other principle-naming I should know about. Lower priority — these are background, not load-bearing for the convergence claim.
- [ ] Bungay Ch 7 — for the executive trinity (directing / managing / leading) and the fourth-locus question. Current disposition (comparative reference, not fourth locus) is unlikely to change based on the verification finding that M1 and O2 aren't fully independent — the *triple* convergence framing was already imprecise, so the paper should pivot to AAT-vs-engineering-family rather than count-of-loci.

### Decision: paper shape revision

Given the verification findings, I'm revising the outline:

- **Section 3 becomes: "The structural identification, AAT side."** Presents the wrapping construction with the two readings (M1: truthification; O2: cascade-recovery) as functions performed by the same construction. The closure-defect quantities $\varepsilon^*_{\text{track}}$ and $\varepsilon^*_{\text{coerce}}$ get explicit definition. The Brooks's-Law tempo cost is named. Honest about prior-art (POMDP, cognitive architectures) — AAT's contribution is the leakage analysis and regime hierarchy, not the wrapping move.

- **Section 4 becomes: "The structural identification, engineering side."** A family of engineering patterns: TodoWrite/TodoRead (Claude Code), LLMCompiler's DAG-with-scheduler, plus operata's explicit naming. Operata is the bridge because it *names* the principle; the others *enact* it. The engineering convergence is itself a small piece of evidence.

- **Section 5 becomes: "The convergence."** Reads the two sides against each other. The structural shape they share. Why the convergence is meaningful (independent paths, different methods, same structure).

- **Section 6 becomes: "Supersession structure (conditional)."** If the identification holds, what engineering consequences follow. E1, E2, E5 traced to which part of the identification forces them.

- **Sections 7 + 8: honest limits + conclusion.** As before.

- **Sections 1 + 2: introduction + problem statement.** Largely unchanged, but section 2 introduces AAT's Class 1/2/3 architectural classification more explicitly because the entire argument turns on the Class 3 boundary.

### Next concrete step

Read the operata principles file briefly (E8 confirmation) and Bungay Ch 7 (fourth-locus closure), then start drafting Section 3 with citations and footnotes. Section 3 first because it sets the voice/depth/citation-density precedent for the rest of the paper.
