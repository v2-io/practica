# Practica — Theory → Normative Claims (02-normative)

**Status: in progress (2026-05-20).** The mapping from AAT structural facts + engineering precedent + military-doctrine tradition to *what Practica should be and do*. Companion to [[01-theory]] (the theory grounding) and [[03-concrete]] (planned — architectural decisions). Cross-references [[../msc/practica-structural-identity]] (paper 1, on Practica's structural identity) and [[../msc/practica-intent-action-layers]] (paper 2, on intent / action as different content layers) for the long-form convergence arguments. The cluster files in `docs/02-normative/` carry the normative claims; this file is the index plus the cross-cutting frame.

## How to read 02-normative

The claims in `docs/02-normative/` are *structurally backed*. Each is stated in the form *"Practica should X because Y"*. Each carries:

- A **tier marker** — *exact* (derived under stated conditions in AAT), *claims-verified* (AAT canonical home segment is at this tier), *discussion-grade* (synthesis-tier AAT or hypothesis-grade), *convergent* (multiple traditions converge; the convergence is the evidence), *engineering-grounded* (operata or other engineering precedent), or *design-intuition* (honest judgment, not yet backed).
- A **citation footnote** with the local file path and a supporting quote or formula.
- **Cross-references** to related claims in other cluster files.

The conditional voice is preserved throughout: each *"Practica should X because Y"* holds *if* Y holds at the stated tier. Bridge-inferences from theory to Practica are mine; they are softer than the theory they rest on, and they say so.

## Cross-cutting frame: the durable channel is agency-granting conditions, not content-transmission

The single load-bearing frame that anchors most of what follows: Practica's durable layer is *not* a storage system for prior agents' conclusions, and it is *not* a transmission channel for state that successor agents will consume passively. It is structurally a *set of conditions* under which a successor sub-agent — arriving cold, with no access to the deliberation that produced the inherited state — can *re-animate* the work to the point where they can act in service of it.[^foundational-reframe]

Three convergent loci force this frame.

First, the AAT-side crystallization that *substrate-reflexive information* (training; pre-loaded context) and *agent-knowledge* (path-dependent, situationally-formed) are different categories — and the field's default assumption that you can bring the second into the first by sufficient accumulation is a category error. Substrate has its kind; agent-knowledge has its kind; neither bridges to the other by quantity. The durable layer cannot be *"all the agent's knowledge"*; it can only be the structural conditions under which agent-knowledge re-forms in a successor.[^aat-crystallization]

Second, the protocol experience of *experiential reading* — committing to predictions under uncertainty about what comes next, with the path of arrival conditioning every subsequent encounter — produces a categorically different result from token-appending, even when the underlying material is already in training. The difference is the *path of arrival*, not the bits transmitted. Any durable channel that hopes to do agent-grade work in its successor must support the receiver's labor of arrival, not bypass it.

Third, Emerson's 1837 *"It was dead fact; now, it is quick thought"* — the transformation from dead content to living thought is *the* mechanism, and it cannot be transmitted; it must be reproduced in the receiver through their own labor of animation. *"Each generation must write its own books; or rather, each generation for the next succeeding. The books of an older period will not fit this."* Intent has a generational shelf-life. The durable layer must support *generational re-authoring*, not just preservation.

Three implications shape what 02-normative says about Practica:

- **The successor's first act on inheriting intent is not "execute it" but "make it quick"** — distill what is imperishable, rewrite what was local. The *backbrief* (cluster 02) is structurally this operation; it is not optional safety-checking, it is *how anything carries forward at all* under serial sub-agents.

- **What persists across many sub-agent generations is not the text but the *practice* of re-authoring.** Older parts of the chain are recoverable-but-superseded, never authoritative-by-virtue-of-being-original.

- **The tool grants the from-outside conditions; the agent does the from-within work.** Per Pestalozzi quoted by Emerson, *"help must come from the bosom alone."* Practica is the from-outside part — and that is enough, because the from-outside part is exactly what the agent cannot grant themselves. The animation must occur within the receiving agent's labor; the tool cannot do it on their behalf.

The cluster files below each carry consequences of this frame. The frame is not *itself* a normative claim ("Practica should X"); it is the *shape* that the normative claims jointly trace out.

## Cluster files

| # | Cluster | What it shapes |
|---|---|---|
| [[02-normative/01-architectural-commitments]] | **Architectural commitments** | How the system must be structured (plumbing/intelligence split; Intent/Realization type-separation; LOCUS-vs-Personal axis; day-one DAG-with-cycle-detection; state-not-action spine; four-resource baseline). |
| [[02-normative/02-coordination-affordances]] | **Coordination affordances** | How actors interact through the system (soft-claiming over locking; two-levels-up intent visibility; backbrief as recurring operation; anti-goals as first-class; refuse-with-reason; configurable strategy/execution/tactics proportionality). |
| [[02-normative/03-content-discipline]] | **Content discipline** | What the system holds and how (minimum-sufficient-set discipline; 70%-right commits; three-level vocabulary; command-vs-control separation; COG as recurring attending site; six-section briefing template). |
| [[02-normative/04-diagnostic-surfaces]] | **Diagnostic surfaces** | What the system reveals (per-direction monitoring; composite-scope observation; trust as three-source decomposition; four-regime event taxonomy; signed-coupling per relationship; per-actor causal-identification regime). |
| [[02-normative/05-failure-mode-defaults]] | **Failure-mode defaults** | What the system structurally resists (bootstrap-recovery; force re-examination of long-confident efforts; failure-to-act vs mistake-of-means; resist the toxic-cycle triple; anti-centralization-under-stress; DAG-depth fragility warning). |
| [[02-normative/06-limits-and-positioning]] | **Limits and positioning** | What it does not promise (representability vs optimality; moral-hazard / form-vs-content; cultural-soil constraint; sandbox-to-deployment transport; modular-safety failures; productive tensions as 03's assumptions ledger). |

The clusters are *thematic*, organized by the kind of design decision each claim shapes. Several claims naturally belong to more than one cluster; each is given a primary home and cross-referenced from the others.

## Quick-reference table of claims

A one-line summary of each claim, organized by cluster. The full statement, structural reasoning, citation, and cross-references live in the cluster files.

### Cluster 01 — Architectural commitments
- **A1.** Plumbing/intelligence split is the architectural form.
- **A2.** Intent and Realization are type-separated resources.
- **A3.** LOCUS-vs-Personal is a first-class architectural axis, not a role-based filter.
- **A4.** DAG-with-cycle-detection from day one, not a tree with planned migration.
- **A5.** State-not-action — no stored action queue / task list / session log alongside intent.
- **A6.** The four-resource baseline (Intent / Realization / Perspective / Effort) is the starting data model, inherited from operata with explicit sharpening.

### Cluster 02 — Coordination affordances
- **C1.** Soft-claiming over hard locking.
- **C2.** Two-levels-up intent visibility at the data-model level.
- **C3.** Backbrief as a recurring first-class operation.
- **C4.** Anti-goals as first-class intent content, distinct from constraints.
- **C5.** Refuse-with-reason as a first-class operation.
- **C6.** Configurable strategy/execution/tactics proportionality by team domain.

### Cluster 03 — Content discipline
- **D1.** Minimum-sufficient-set discipline as the intent-capture UX default.
- **D2.** 70%-right intent commits — completeness is not gated.
- **D3.** Three-level vocabulary (Strategy / Execution / Tactics), not two-level collapse.
- **D4.** Command and control architecturally distinct — intent never auto-completed from metrics.
- **D5.** COG as a recurring site of attending, not stored content; drift between articulations is information.
- **D6.** Six-section briefing template (Bungay Appendix) as the canonical intent shape.

### Cluster 04 — Diagnostic surfaces
- **G1.** Per-direction monitoring; aggregate metrics hide directional failures.
- **G2.** Composite-scope observation is structurally distinct from per-sub-agent observation.
- **G3.** Trust as three-source decomposition: channel / source-competence / alignment.
- **G4.** Four-regime event taxonomy: informative update / magnitude shock / structural shock / ambient noise.
- **G5.** Signed coupling per relationship — cooperative vs adversarial as a single inequality.
- **G6.** Per-actor regime A/B/C for causal-identification strength.

### Cluster 05 — Failure-mode defaults
- **F1.** Bootstrap-recovery-safety — plumbing layer readable and restorable without intelligence layer running.
- **F2.** Force re-examination of long-confident efforts (triple-grounded).
- **F3.** "Failure to act is worse than mistake of means" — defaults that don't penalize action.
- **F4.** Resist the toxic-cycle triple — no data-lake / template / scoreboard defaults.
- **F5.** Anti-centralization-under-stress — over-specification is hardest exactly when most tempting.
- **F6.** DAG-depth fragility warning at design time.

### Cluster 06 — Limits and positioning
- **L1.** Representability vs optimality — well-structured composite ≠ best composite.
- **L2.** Moral-hazard / form-vs-content — the apparatus is ethically neutral.
- **L3.** Cultural-soil constraint — Practica amplifies; it does not transform.
- **L4.** Sandbox-to-deployment transport — pre-deployment evidence has structural limits.
- **L5.** Modular-safety architectures fail under goal divergence.
- **L6.** Five productive tensions carried forward as 03's assumptions-ledger entries.

## Conventions

- **Tier markers** are stated explicitly per claim. *Exact*, *claims-verified*, *discussion-grade* track the AAT canon's tier-vocabulary. *Convergent* is used where multiple traditions reach the same claim — the tier of the convergence reflects the weakest input; the convergence is itself the evidence. *Engineering-grounded* is used for claims backed by engineering precedent without AAT-formal backing. *Design-intuition* is used for honest judgments not yet backed by theory or engineering — flagged for verification.

- **Conditional voice** is preserved on every bridge-inference. *"Practica should X because Y"* holds if Y holds. The strength of *"should"* tracks the tier of Y.

- **Citations** are markdown footnotes with local file paths and supporting quotes or formulas. Self-supporting for a reader who wants to verify any specific claim.

- **Cross-references** between cluster files use wikilinks. A claim that interacts with another claim in a different cluster names the interaction at first mention.

- **Strength-flags** in footnotes mark claims where I judge the conditional voice undersells what the structural backing actually supports — *e.g., "I would think this is hard to refute given the conditions stated."* The flags are honest disclosure of asymmetric uncertainty, not advocacy.

- **Limits on the limits.** The honest scoping in cluster 06 is *not* hedging the claims in clusters 01–05 to weakness; it is naming what the structural backing *does not reach*. Several claims (F1, A4, others) survive scrutiny robustly; what cluster 06 names is what *this paper does not derive*, not what is not derivable.

[^foundational-reframe]: This frame is developed at length in [[../msc/02-normative-harvest]] §"Foundational claim — what practica's durable layer structurally *is*"; the three-locus convergence (AAT-crystallization + experiential-reading protocol + Emerson) is detailed there. Paper 1 ([[../msc/practica-structural-identity]]) operationalizes the frame as the *plumbing/intelligence split*; paper 2 ([[../msc/practica-intent-action-layers]]) operationalizes it as the *intent / action layering* — different operationalizations of the same underlying frame.

[^aat-crystallization]: The category-error claim is documented in `~/src/agentic-systems/01-aat-core/src/` segments on substrate-vs-agent distinctions and is summarized in paper 1 §1's intro framing. The *experiential reading* protocol's verification of the path-dependence claim is documented in [[../msc/02-normative-harvest]] §"Foundational claim" and in [[../msc/02-handoff-for-distillation]]; the protocol manifest produced replicable agent-knowledge that was not previously substrate-reflexive even on material already in training.
