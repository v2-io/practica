# Alignment-autonomy 2×2 — comparative descriptive paper (s5 working)

**Working substrate.** Iteration channel for paper 2 (the loci paper). Companion to paper 1 at [[../practica-structural-identity]]; same iteration shape and voice discipline.

## Premise (first-pass, conditional)

**Convergence claim under examination.** *Intent* (binding across the composite, aligned per actor) and *action* (free across the composite, autonomous per actor) live at different content layers. The conventional framing presents alignment and autonomy as endpoints of a single trade-off axis; the alternative framing presents them as orthogonal axes that *reinforce* each other — high alignment on intent (what + why) enables and is enabled by high autonomy on action (how). The 2×2 is not a stylistic preference; it has been independently identified across multiple traditions:

- **Military doctrine — Moltke 1869**, *Guidance for Large Unit Commanders*: an order should contain *"all, but also only, what subordinates cannot determine for themselves to achieve a particular purpose."* The minimum-sufficient-set discipline carries the principle. Operationalized through *Auftragstaktik* / mission command across the Prussian and later German general staff tradition.

- **Management theory — Bungay 2011**, *The Art of Action*: Ch 3 Figs 7→8 explicitly historicizes the trade-off axis and replaces it with the 2×2 ("directed opportunism"). Synthesizes Moltke and the Prussian military tradition for business-management practice. *Not an independent locus* from Moltke — Bungay carries the doctrine forward; the lineage matters for honest convergence-counting.

- **AAT formalism — three partially-related formulations**:
  - `der-action-selection`: action is *derived from state* each cycle, never stored — Section I scope, exact within scope.
  - `hyp-auftragstaktik-principle`: information-bottleneck-derived inter-agent bandwidth allocation $B_O \gt B_\Sigma \gt B_M$ — invest in *objective sharing* first, then *strategy coordination*, then *model synchronization*. Hypothesis-grade.
  - `der-orient-cascade` (paper 1, §3.5 verified): cascade ordering forced by information dependency — $M_t \to A_O \to \Sigma_t \to O_t$, objective-revision last. Claims-verified.
  
  These three are *not three independent loci within AAT*; they are three formulations from different parts of the AAT machinery that point at the same structural fact. The within-AAT independence question is exactly what Joseph said this session would help test. I will frame them honestly as *three readings within AAT*, not three independent identifications.

- **Engineering — operata**: Intent and Realization as structurally separated resources. Intent records hold *desired state* (binding, can be shared / aligned across actors); Realization records hold *what happened versus expected* (per-actor execution traces, freely chosen approach). The data-model separation pre-dates the AAT formalism and was reached through engineering necessity, not theory.

**Honest convergence count.** The harvest's "six-locus" framing is over-count if loci must be *truly independent*. The honest count is **three traditions** — military doctrine (Moltke → Bungay), AAT formalism (with three partially-related internal formulations), engineering (operata). The within-AAT formulations are evidence that the principle has multiple analytical entry points within the formalism; they are not independent corroborations of it. The three traditions, however, *are* independent — different methods, different historical lineages, different failure modes.

**Normative claim under examination.** *If* the alignment-autonomy 2×2 captures a structural fact about composite coordination, *then* practica's data model and UX defaults must reflect the asymmetry — intent layer aligned-and-shared across actors; action layer free-and-per-actor; specific affordances (two-levels-up intent visibility, a six-section briefing template, anti-goals as first-class, backbrief as recurring re-authoring) fall out as consequences of honoring the 2×2 under serial sub-agent + context-turnover conditions.

The normative claim is a design directive that follows from the convergence; it is conditional in the same sense paper 1's supersession structure was conditional.

## Relationship to paper 1 (the structural-identity paper)

Paper 1 (`msc/practica-structural-identity.md`) established what Practica is *structurally* — a truthification scaffold for serial sub-agents using Class 3 substrates, with a plumbing/intelligence split. The four shared structural commitments (S1)–(S4) are the structural identification.

Paper 2 is about what Practica *coordinates* — specifically, the structure of intent-versus-action content the plumbing layer holds. Paper 2's normative claims rest on paper 1's structural identification: the alignment-autonomy 2×2 is what the plumbing layer should encode, and the engineering consequences of paper 1 (E1 bootstrap-recovery, E2 soft-claiming, E5 day-one DAG) provide the substrate on which paper 2's normative claims operate.

The two papers are independent in their arguments but mutually informing in their conclusions. Paper 2 will reference paper 1 where the architectural commitments are presupposed, but the alignment-autonomy claim does not depend on paper 1's identification — it could hold under different architectural commitments. Conversely, paper 1's structural identification does not specify what content the plumbing layer holds; paper 2 supplies that.

## Audience and voice

Same as paper 1. Highly-literate but general peers; mild AAT familiarity; markdown footnotes with local file links and supporting quotes; calibrated voice with strength-flags in footnotes where warranted; conditional throughout.

## Rough outline (placeholder — refine after source reads)

1. **Introduction.** Practica's stated goal. The question this paper takes up: how should intent and action be structured in a coordination substrate for composite work? Conventional framing as a trade-off; the 2×2 alternative; preview of the convergence.

2. **Problem: the alignment-autonomy framing.** The conventional trade-off axis. The 2×2 reframing. Why the difference matters for practica.

3. **The military-doctrine identification (Moltke 1869 + Bungay 2011).** Auftragstaktik / mission command. The minimum-sufficient-set discipline. Moltke 1871 *"On Strategy"* (in Bungay Appendix) for primary text. Bungay's contribution: the explicit 2×2 (Figs 7→8) and the strategy-briefing template.

4. **The AAT formalism (three partial readings).** `der-action-selection` (state-not-action); `hyp-auftragstaktik-principle` (IB bandwidth allocation $B_O > B_\Sigma > B_M$); `der-orient-cascade` (cascade-ordering, objective-revision-last). Honest framing: these are not three independent identifications but three formulations from different parts of the formalism. The fact that multiple AAT entry points reach the same conclusion is evidence about the principle's structural depth, *not* about loci-count.

5. **The engineering identification (operata's Intent vs Realization).** Pre-theory data-model separation. Intent records cross-cut actors; Realization records are per-actor execution traces. The engineering arrived at the asymmetry by necessity — execution-mode and planning-mode require different cognitive registers (operata's own "Cognitive Modes" working note).

6. **The convergence.** Three traditions, with AAT contributing multiple internal formulations. What the traditions share. The disjoint-failure-modes argument (similar to paper 1's §5.4 but adapted to this convergence). Honest scoping of the convergence count.

7. **Normative implications (conditional).** *If* the 2×2 captures a structural fact, several design directives follow for practica: cross-cutting intent layer; per-actor action layer; two-levels-up intent visibility (Bungay Ch 5); six-section briefing template as canonical intent shape (Bungay Appendix); anti-goals as first-class content (Bungay Ch 5); the backbrief as recurring re-authoring (cross-reference to paper 1's foundational reframe). The directives are entailments, not derivations.

8. **Honest limits + Conclusion.** What this paper does and does not establish. Convergence-count honesty (three traditions, not six loci). AAT-tier limits inherited from paper 1. Operata as engineering-convicted-of-shape. Future work.

## Source-verification checklist (read-before-promote)

**AAT canon — required reads (specific to paper 2):**
- [ ] `~/src/agentic-systems/01-aat-core/src/der-action-selection.md` — the action-derived-from-state-each-cycle home segment. Verify the *"never stored"* framing and the Section I scope.
- [ ] `~/src/agentic-systems/01-aat-core/src/hyp-auftragstaktik-principle.md` — the IB-bandwidth-allocation home. Verify the $B_O > B_\Sigma > B_M$ ordering, the regime-reversal honesty (under genuine ambiguity, model-sync may matter more).
- [ ] `~/src/agentic-systems/01-aat-core/src/def-strategy-dimension.md` — possibly relevant for the intent-action vocabulary.
- Already read from paper 1: `der-orient-cascade.md`, `der-directed-separation.md`, `der-class-coercion-via-wrapping.md`.

**Bungay — required reads:**
- [ ] `~/src/_ref/books/Art-of-Action/parts/03-elements-of-a-solution.md` or wherever Ch 3 lives — Figs 7→8, the trade-off vs 2×2 reframing.
- [ ] `~/src/_ref/books/Art-of-Action/Art-of-Action.md` Appendix — Moltke 1871 *"On Strategy"* full translation; the strategy-briefing template six-section form.
- [ ] `msc/s3-working/03-the-solution.md` and `msc/s3-working/05-strategy.md` — per-chapter working papers, may have the §4 *applicability* content useful for the engineering-implications section.

**Operata — already verified in paper 1:**
- `~/src/operata/docs/glossary.md` — Intent + Realization + Perspective + Effort definitions.
- `~/src/operata/TODO.md` — §"Cognitive Modes: Intent vs Action" specifically for paper 2.

**Other:**
- [ ] Moltke 1869 *Guidance for Large Unit Commanders* — primary source. Probably cited via Bungay; direct text access uncertain. Note honestly if accessed only through Bungay's quotation.

## Open questions to resolve before first draft

1. **Within-AAT independence of the three formulations.** Are `der-action-selection`, `hyp-auftragstaktik-principle`, and `der-orient-cascade` *three independent loci* or *three readings* of the same principle? Current disposition: three readings, not three loci. Will verify after reading the home segments. *This is the question Joseph said this session would help test, so I should be especially careful here.*

2. **Moltke / Bungay independence.** Current disposition: not independent — Bungay carries Moltke forward, the lineage is acknowledged in Bungay's own attributions. Treat as one tradition (military doctrine) with Moltke as primary and Bungay as synthesis. The convergence count is *not* improved by counting them separately.

3. **Operata's "Intent vs Realization" mapping.** Is this *the same principle* as alignment-autonomy 2×2, or a *different distinction* that happens to align with it? Operata's Intent ≈ desired-state; operata's Realization ≈ what-happened. The mapping: Intent corresponds to the *binding/aligned* axis (states everyone agrees we want); Realization corresponds to the *free/autonomous* axis (per-actor execution traces, whatever approach was taken). This is a plausible mapping but should be examined carefully.

4. **Convergence-count honesty.** The harvest claimed "quadruple" → "quintuple" → "sextuple" convergence as the sweep progressed. Honest count is three traditions (with internal multiplicity in AAT). Should the paper explicitly address the over-counting? *Disposition for now:* yes — name the harvest's count, acknowledge the over-count, and state the honest count. This is the kind of cross-cycle correction that future agents working with this material will benefit from seeing.

5. **Normative implications scope.** Bungay's strategy-briefing template (six sections), anti-goals, and two-levels-up visibility are all specific design directives. They follow from the 2×2 under conditions but are also content-rich. How much specific design content should paper 2 carry?

   - *Option A (minimalist):* paper 2 establishes the convergence and states the normative claim abstractly; specific design directives are left for 03 (the architecture/requirements doc planned for practica).
   - *Option B (substantive):* paper 2 traces specific design directives as conditional entailments, similar to paper 1's E1/E2/E5 trace.
   - *Disposition for now:* B. The first paper traced three specific design consequences; paper 2 should trace its own specific normative implications to be parallel and useful.

6. **The "third source"** Joseph mentioned but didn't specify by name. From paper 1's harvest context, Source 3 was Bungay's *Art of Action* — meaning Bungay is already on my list, not a fourth source. Confirm.

## Process

- **This iteration:** the working file (you are reading it).
- **Next iteration:** read the AAT home segments + Bungay Ch 3 + Bungay Appendix. Update working notes with verified vs unverified claim status.
- **Then:** draft sections, starting with one that establishes voice/depth (probably §3 Military-doctrine identification, since the historical material has different texture from paper 1's AAT-formal lead).
- **Then:** remaining sections, one or two per iteration.
- **Then:** adversarial pass + Truth/Honesty judgment + assembly.

## Failure modes to watch (carried forward from paper 1, plus paper-2-specific)

Carried forward: voice (calibrated humility), supersession conditionality, audience scope-tightness, pedagogical inflation, convergence-stretch.

Paper-2-specific:
- **Over-counting loci.** The harvest's "six-locus" framing is the failure mode itself. Don't reproduce it. State honest count.
- **Conflating the Bungay/Moltke tradition with AAT's IB-derived bandwidth.** They reach the same operational conclusion ($B_O > B_\Sigma > B_M$) but the *derivations* are different — Bungay is historical-empirical, AAT is information-theoretic. The convergence is *on the conclusion*; the *derivations* are independent.
- **Treating the 2×2 as universally applicable.** Bungay explicitly notes regime-reversal: under genuine ambiguity (fog of war, unprecedented conditions), model-sync may matter more than objective-sharing. The 2×2 is regime-conditional. Paper 2 must carry this honestly.
- **Conflating intent-vs-action with paper 1's plumbing/intelligence split.** These are different cuts. The plumbing/intelligence split is about *who has the judgment* (deterministic substrate vs. LLM); the intent-vs-action split is about *what kind of content the system holds* (desired states vs. execution traces). They interact but are distinct axes.

---

## Verification log — round 1 (after AAT source reads + Bungay Ch 3 working paper)

### What verified solidly

- **`der-action-selection` is *exact within Section I scope*, deps-verified stage.** This is HIGHER tier than I had expected. The claim $a_t = \pi(M_t)$ — action is a function of the agent's complete internal state — follows from `form-agent-model`'s completeness commitment. The Section II lift to $a_t = \pi(M_t, G_t)$ is also exact under the same completeness argument. *Action is not stored; action is derived from state each cycle.*
  - Important contextual detail: the discussion distinguishes *implicit* action selection (model-embedded, Boyd's IG&C, expert intuition) from *explicit* deliberation (System 2, planning, MCTS). The implicit/explicit distinction is discussion-grade.
  - The exactness is foundational: this is one of the most strongly-tiered claims in the AAT canon.

- **`hyp-auftragstaktik-principle` is *discussion-grade* hypothesis, draft stage.** Max attainable: *empirical*. The $B_O > B_\Sigma > B_M$ ordering is a qualitative prediction grounded in the IB framework and supported by military-organizational evidence; the formal IB derivation has NOT been completed. The source explicitly says: *"the IB optimization would need to be solved explicitly with realistic cost functions to confirm the ordering."*
  - **Regime-reversal honesty.** *"When the environment is genuinely ambiguous and local observations are insufficient (fog of war, novel codebase, unprecedented market conditions), model synchronization may be worth more than objective sharing — sub-agents who share the same wrong model at least err consistently, which is sometimes better than each having a different wrong model."* This must be carried in paper 2.
  - This means the convergence on $B_O > B_\Sigma > B_M$ between AAT-hypothesis and Bungay-empirical is *not* "AAT derives Moltke's empirical observation." It is "AAT hypothesizes a formal mechanism, supported by the same empirical evidence Moltke observed." Paper 2 must be careful with this.

- **Bungay Ch 3 working paper confirms** the Fig. 7 → Fig. 8 reframing as the chapter's central conceptual move; the Moltke 1869 minimum-sufficient-set quote; the Meckel 1877 *"intention was binding; the task was not"* distinction; the *selbstständig denkender Gehorsam* (independent thinking obedience) synthesis; the cascade structure; the 70% rule; backbriefing as Fig. 9 alignment-gap mechanism. The §4 *Applicability to Practica* section in the working paper has rich material for paper 2's §7 (normative implications).

### What shifted — important reshape

**The three AAT "formulations" are NOT three independent loci. They are one foundational claim + two derived consequences.** The honest within-AAT structure:

1. **`der-action-selection` is foundational** — *exact-within-scope* tier. Action is a function of state, not stored. This is upstream of everything else.

2. **`der-orient-cascade` is a downstream consequence** — *claims-verified* tier. Given action-from-state, the *resolution* of mismatch types follows a forced ordering (epistemic update → attainability → strategy → objective).

3. **`hyp-auftragstaktik-principle` is also downstream, weaker tier** — *discussion-grade hypothesis*. Given action-from-state plus the IB framework, the *bandwidth* allocation for inter-agent communication prioritizes objectives.

All three share machinery (the directed-separation / state-not-action structure from §3 of paper 1). The cascade and bandwidth claims are *applications* of the action-from-state foundation. They reach different *kinds* of conclusions (resolution order, sharing priority) from the same foundational structure.

**This means the honest convergence count is even simpler than my initial framing.** The AAT side contributes *one* foundational claim (state-not-action / action-from-state) plus *two* applications. The traditions converging are:

- **AAT formalism** (one foundational claim + two applications, internal multiplicity within)
- **Military-doctrine tradition** (Moltke 1869 + Bungay 2011, one tradition)
- **Engineering** (operata's Intent/Realization separation)

**Three traditions, not six loci.** The harvest's count was loose; paper 2 should correct it explicitly in §6.

### The strongest convergence claim, restated

*Intent (binding, aligned across actors, persistent across context-turnover) and action (free, autonomous per actor, derived from current state) live at structurally different content layers.* This has been independently identified by:

- AAT, formally derived as `der-action-selection` (exact-within-scope): action is a function of state, not stored.
- Military doctrine (Moltke 1869, codified in *Auftragstaktik* / mission command; synthesized for management practice by Bungay 2011 as the alignment-autonomy 2×2): "the intention was binding; the task was not."
- Engineering (operata's Intent + Realization as structurally separated resources): pre-theory crystallization that intents hold *desired state* while realizations hold *what happened*.

The convergence is on *the structural separation*. The convergence on the *priority ordering* ($B_O > B_\Sigma > B_M$) between AAT-hypothesis and military-empirical is weaker — both are at empirical / hypothesis tier, with explicit regime-reversal conditions. Paper 2 should separate these two convergences in its structure: the foundational separation as the main claim; the bandwidth priority as additional structure with lower-tier scoping.

### Revised section plan (after verification)

The eight-section structure stays, but section 4 (AAT) reshapes:

- **§4.1** introduces `der-action-selection` as the foundational claim — exact-within-scope tier, the strongest in the chain.
- **§4.2** introduces `der-orient-cascade` as the resolution-order consequence — claims-verified tier, derived in paper 1.
- **§4.3** introduces `hyp-auftragstaktik-principle` as the bandwidth-allocation hypothesis — discussion-grade with explicit regime-reversal honesty.
- **§4.4** names the within-AAT structure honestly: one foundational claim + two consequences, sharing machinery; not three independent identifications.

Section 6 (convergence) will then frame the cross-tradition convergence cleanly as **three traditions**, with the AAT-internal multiplicity acknowledged but not counted.

Section 7 (normative implications) can draw on the rich §4 *Applicability* section of the Ch 3 working paper — backbriefing, minimum-sufficient-set, 70%-rule, anti-centralization-under-stress, "refuse-with-reason" first-class operation, configurable proportionality.

### Methodological notes carried forward from paper 1

- **Voice discipline:** tier marks visible (`derived`, `claims-verified`, `discussion-grade`); bridge-uncertainty explicit on every "this implies"; strength-flags in footnotes where the conclusion is firmer than surface text shows.
- **Citation discipline:** local file paths + verbatim quotes in footnote bodies.
- **Honest scoping:** AAT-side tier limits visible; engineering side *convicted-of-shape*, not *validated-by-production*; convergence-count honesty.
- **Section ordering:** for paper 2, the *military-doctrine identification* (§3) comes before the *AAT formalism* (§4), because Moltke 1869 is the primary historical source and the chronological order (Moltke → Bungay → operata → AAT) is the natural read.
- **Working-doc artifacts:** for paper 2, write each section file with the proper heading levels for assembly (no top-level working header that needs stripping). This eliminates the awk/sed concatenation step from paper 1.
- **Read efficiency:** trust per-chapter working papers (s3-working/) for Bungay quotations where the prior agent's fidelity has been verified, rather than re-reading the book chapter directly. Honest citation: cite Bungay primarily, via the working paper as intermediate verifier.

### Still pending (low priority)

- Direct verification of Bungay Ch 3 specific quotes from the book chapter file (the working paper has the verbatim quotes; this would be additional verification). Skip unless drafting hits a passage where exact wording matters more than the working paper provides.
- Moltke 1871 *"On Strategy"* from the book Appendix. The 1869 *Guidance* is the primary source for paper 2; the 1871 essay is supplementary. Skip unless §3 (military-doctrine) needs the primary text for a specific claim.

### Next concrete step

Update tasks; start drafting §3 (military-doctrine identification) first to set voice/depth/citation-density precedent for paper 2. The historical material has different texture from paper 1's AAT-formal lead, and getting the voice right for that texture first is the right precedent.
