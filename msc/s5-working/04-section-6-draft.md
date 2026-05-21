## 6 — The convergence

Three traditions reach the alignment-autonomy 2×2 by different paths. *Military doctrine* (Moltke 1869 → Bungay 2011) arrived empirically through a century-plus of operational practice; the doctrine names *intent binding, task free* as the operational structure that makes large-scale composite coordination tractable. *AAT formalism* (`der-action-selection`) derived the structure formally from a completeness commitment on the agent's internal state — action is a function of state, not stored. *Engineering* (operata's Intent / Realization data-model separation) reached the structural cut by the friction of trying to build a coordination system that could not collapse the two layers.

What the three traditions share, where they differ, what the convergence is and is not — these are this section's content. The honest convergence count matters, and is addressed directly: this is *three traditions*, not the *quintuple* or *sextuple* the harvest framing implied.

### 6.1 What the three traditions share

The shared content is more compact than paper 1's four structural commitments. The alignment-autonomy 2×2 reduces to a single structural fact stated in each tradition's vocabulary:

| Tradition | Statement of the same structural fact |
|---|---|
| Military doctrine (Moltke / Bungay) | *"The intention was binding; the task was not."* Intent (what + why) aligned; action (how) free. |
| AAT formalism | $a_t = \pi(M_t, G_t)$ — action is a function of the complete internal state, derived each cycle. State and action live at different content layers by completeness. |
| Engineering (operata) | Intent (desired state) and Realization (what happened) are type-separated resources. Intent records do not carry execution traces; Realization records do not carry goal content. |

Three vocabularies; one structural cut. *Intent is durable, sharable, and binds. Action is per-actor, per-moment, and derived from current state.* The three traditions agree on this central content. They differ on what they each *add* beyond the central content — §6.2 traces the specifics.

### 6.2 Specific correspondences (and asymmetries)

The correspondences across the three traditions, with the asymmetries flagged:

| Concept | Military doctrine | AAT formalism | Engineering (operata) |
|---|---|---|---|
| The structural cut | Intent / Task (Meckel 1877) | State / Action (`der-action-selection`) | Intent resource / Realization resource |
| The cut's status | Empirical-doctrinal; operationally proved over 150 years | Derived from completeness, *exact within scope* | Data-model enforcement; engineering-pre-theory |
| Specification discipline | *"All but only what subordinates cannot determine"* (Moltke 1869) | Minimum-sufficient-set is implicit in $\pi(M_t)$'s economy | *"Inversion enables back-planning"* — Intent describes states, not actions |
| Resolution-order discipline | Cascade with backbrief; objective revision last | `der-orient-cascade` proves the ordering forced by information dependency | Not articulated; would have lived in the unbuilt Session layer |
| Bandwidth-allocation priority | *$B_O > B_\Sigma > B_M$* (empirical, military-organizational evidence) | *$B_O > B_\Sigma > B_M$* (IB-hypothesis, regime-conditional) | Not explicit in operata's documentation |
| Regime-reversal conditions | Not explicit in 1869 *Guidance*; partially implicit in cascade fallback | Explicit: under genuine ambiguity, model-sync may dominate objective-sharing | Not addressed |
| Cultural / trust prerequisite | Explicit: "the cultural-soil constraint" (Ch 3 closing) | Not addressed directly | Implicit in the team-collaboration assumption; not articulated |

Several asymmetries matter. The military-doctrine tradition has the *richest operational vocabulary* — the cascade, backbriefing, freedoms and constraints, the 70% rule, the cultural-soil constraint. AAT supplies the *firmest derivation* of the central cut (exact within scope) but adds less operational detail. Engineering supplies the *cleanest data-model realization* of the central cut but has the weakest articulation of resolution and cultural-soil conditions. Each tradition has texture the others lack. *The convergence is on the central cut; the differential texture is where the traditions complement each other.*

The bandwidth-allocation priority — the $B_O > B_\Sigma > B_M$ ordering — is in a different category from the central cut. It is shared by the military-doctrine tradition (operationally) and AAT (as hypothesis), but *both are empirical-grade in their current form*. The military-doctrine claim is grounded in operational practice; the AAT claim is grounded in IB-framework reasoning supported by the same operational evidence. The convergence on this priority is weaker than the convergence on the central cut, and §6.5 addresses its regime-conditional limits.

### 6.3 The convergence-count clarification

The harvest that fed this paper named the convergence variously as *quadruple*, *quintuple*, and *sextuple* as additional AAT segments were added across the sweep. Reading the source material carefully, this count is loose. The honest count, after the verification work of §3–§5, is **three traditions**. Here is the accounting:

| Harvest-claimed locus | What it actually is |
|---|---|
| Moltke 1869 *Guidance for Large Unit Commanders* | Primary source within the military-doctrine tradition |
| Bungay 2011 *The Art of Action* | Synthesis-and-historicization of Moltke for management practice; *carries Moltke forward*, not independent |
| AAT `der-action-selection` | State / action layering result — *exact within scope* |
| AAT `der-orient-cascade` | Resolution-order result — *claims-verified*; sister derivation to action-selection on the same Section II substrate |
| AAT `hyp-auftragstaktik-principle` | Bandwidth-allocation hypothesis — *discussion-grade*; sister derivation to the other two on the same Section II substrate plus IB framework |
| Operata Intent / Realization separation | Engineering data-model crystallization |

Reduced honestly: military doctrine is *one* tradition with two voices; AAT contributes *three sister applications of one shared substrate* (Section II agent-model with directed separation) — not three independent loci within AAT, but also not a strict consequence-chain; engineering is *one* tradition (operata). **Three traditions, not six.**

This clarification matters in two directions. *Downward*: a count of six suggests stronger evidentiary backing than the structural argument actually has, and pretending otherwise inflates the argument's weight. *Upward*: a count of three is itself non-trivial — three independent traditions, by genuinely different methods, reaching the same central cut is meaningful evidence; the corrected count is still strong, just *honestly* strong rather than *misleadingly* strong.[^count-correction-strength]

### 6.4 Why the convergence is meaningful evidence

Three reasons. They are similar to paper 1's §5.4 but adapted for this convergence.

**First: disjoint-failure-modes across the three traditions.** Military doctrine's failure modes are about historical contingency (would a different military culture have arrived at a different structure?) and operational selection (did the doctrine survive because it works, or because Prussia/Germany was already structurally advantaged?). AAT's failure modes are about formal-derivation choices (does the completeness commitment on internal state import the conclusion, or is it earned from independent assumptions?). Engineering's failure modes are about framework-author preferences and tooling constraints (would different framework authors have chosen different decompositions?). The three sets of failure modes are largely disjoint — what would lead one tradition astray would not lead the others astray. When three methods with disjoint failure modes converge on the same central cut, the cut is more likely structurally forced than method-artifactual.

**Second: the central cut is non-obvious.** Many task-coordination systems collapse intent and action into a single content layer ("tasks" carry both purpose and procedure). Many management writing-style guides treat alignment and autonomy as a single trade-off axis (Bungay's Figure 7 strawman is real — it is what most management-practice writing actually does). Many engineering attempts at coordination tools start with a unified data model and discover the friction later (operata's *Cognitive Modes* working note is the friction recorded). *The 2×2 reframing is not what working systems default to; it is what they reach for after the failures of the unified-layer framing become visible.*

**Third: the convergence has design content.** §7 traces specific normative implications that fall out of the central cut — the data-model separation between intent records and execution traces; the two-levels-up intent visibility from the cascade structure; the six-section briefing template that operationalizes the minimum-sufficient-set discipline; the backbrief as the recurring alignment-verification mechanism; anti-goals as first-class content. These design implications are coherent as a set *because* they all flow from the central cut. The convergence has predictive content: certain design choices that look like independent preferences become entailments under the structural identification.

### 6.5 Where the convergence stops

Three limits, named honestly before §7 takes up the normative implications.

**The bandwidth-allocation priority is regime-conditional.** The $B_O > B_\Sigma > B_M$ ordering is the convergence's weakest link. Both the military-doctrine tradition and AAT acknowledge regime-reversal conditions — under genuine ambiguity (fog of war; unprecedented conditions; novel domains), model-synchronization may dominate objective-sharing. The convergence on this priority is on the *typical regime*, not on a universal ordering. Paper 2 must carry this when drawing normative implications from the priority — it is a default, not a universal.

**The structural cut is silent on cultural prerequisites.** Bungay's cultural-soil constraint (§3.6) is real and load-bearing: mission command does not transfer into organizations whose existing culture cannot support it. The AAT formalism does not address cultural prerequisites; operata's engineering identification does not articulate them. The central cut is *necessary* for composite coordination under conditions like Practica's; it is not *sufficient*. A team adopting tooling built on the cut will get value bounded above by the cultural soil's tolerance for trust, honest mistakes, and freedom-within-bounds.

**The cut does not specify implementation.** Three traditions agree on the central separation but disagree on (or are silent about) specific implementations. Moltke's six-section briefing template is one operationalization; operata's four-resource decomposition is another; AAT does not prescribe a specific implementation. The convergence is on *what the system must structurally distinguish*; it is not on *what the implementation must look like*. §7 traces normative implications carefully — naming what follows structurally versus what is one specific instantiation among several.

[^count-correction-strength]: The correction from "sextuple convergence" down to "three traditions" is itself a worked example of the kind of cycle-cleanup the methodology in paper 1 (and the global voice discipline) demand. The original count was reached by good-faith accumulation across a sweep that lacked enforced re-examination of the locus boundaries. Naming the over-count explicitly here, and tracing the honest count, is the correction. I would think this is fairly hard to refute — the lineage claims (Moltke / Bungay as one tradition; the AAT chain as foundation + consequences) are textual and citable — but I want to be explicit that the correction was reached through verification of the sources, not by softening from a strong claim toward a weaker one. The "softening" reading would be wrong; this is *replacement of a loose count with the right one*.
