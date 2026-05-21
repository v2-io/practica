## 8 — Honest limits and conclusion

This paper has presented a comparative-descriptive reading of three traditions' independent identifications of the alignment-autonomy 2×2, addressed the convergence count honestly, and traced four normative implications for Practica as conditional entailments. The voice has been calibrated throughout. This closing section names the limits more directly than the body sections have, so the reader can locate where the paper's argument stops and where future work would need to continue.

### 8.1 What the military-doctrine side does not establish

Two limits.

*The doctrine is empirical-historical, not formally derived.* Moltke did not derive the 2×2 from first principles; he discovered it through Prussian-army operational practice between 1857 and 1888 and consolidated it in the 1869 *Guidance*. Bungay's 2011 synthesis historicizes the doctrine for management practice without supplying a formal derivation. The military-doctrine identification's strongest claim is *empirical*: the doctrine has worked, repeatedly, under specifiable conditions. A reader who wants a formal derivation must look to the AAT side (§4); the military-doctrine side supplies operational evidence and articulated mechanism (cascade, backbrief, freedoms and constraints), not a derivation.

*The cultural-soil constraint is load-bearing.* Bungay's Ch 3 closing pages name the constraint: mission command does not transfer into organizations whose existing culture cannot support it. The named barriers are *risk aversion* and *careerism*. The cultural prerequisite is *trust* across the hierarchy, both up and down, and trust requires constant work to build and is fragile. Practica deployed in an organization without that cultural soil will produce a *dead form* — the apparatus in place, the structural separation in the data model, the affordances available — but without the trust substrate, the form will not animate. This is not a problem the structural identification can solve; it is a limit of when the structural identification can be acted on.

### 8.2 What the AAT side does not yet establish

The AAT segments cited in §4 are at different tiers.

- `der-action-selection` is at *exact within Section I scope*, *deps-verified* stage. This is the strongest AAT result this paper draws on. The structural cut between state and action is firmly grounded.
- `der-orient-cascade` is at *claims-verified* (verified in paper 1, §3.5). The cascade *ordering* is exact; the *timing* is not derived.
- `hyp-auftragstaktik-principle` is at *discussion-grade hypothesis*. The $B_O > B_\Sigma > B_M$ ordering is a qualitative prediction grounded in the IB framework, supported by military-organizational evidence, but *not derived* — the source explicitly notes that *the IB optimization would need to be solved explicitly with realistic cost functions to confirm the ordering*.

The aggregate AAT-side claim — that the alignment-autonomy 2×2 follows from foundational AAT machinery — rests at the *strongest* tier of `der-action-selection` for the structural cut, and at the *weakest* tier of `hyp-auftragstaktik-principle` for the bandwidth-allocation priority. Future work that closes the IB derivation under realistic cost functions would lift the bandwidth-priority claim to derived tier; until then, that part of the AAT side remains empirical.

A second limit: the AAT formalism is silent on cultural prerequisites. The Section I and Section II machinery operate on adaptive agents under specified conditions; *cultural fit*, *organizational trust*, and similar conditions are outside the formalism's scope. The AAT side strengthens the structural cut and adds derivation-rigor; it does not address when the cut is adoptable.

### 8.3 What the engineering side does not establish

The same convicted-of-shape / not-validated-by-production scoping as paper 1. Operata's 30/30 BDD-green status at abandonment is non-trivial — the engineering contracts held under test — but sustained production use would have exposed integration failure modes and edge cases that pre-production engineering does not surface. The data-model separation between Intent and Realization is verified at the contract level; the broader design has not been validated by sustained operational use.

A more specific limit, recorded in operata's own voice: the *Cognitive Modes* tension between intent-oriented framing and execution-mode framing was *named* but *unresolved* at operata's abandonment. Three possible resolutions were sketched; none were chosen. Operata's engineering identification is therefore evidence that the friction is real and structural, *not* evidence that operata had a refined design for handling it. A successor implementation of Practica that ships the Intent / Realization separation may inherit the same friction unless it also resolves the planning-vs-execution cognitive-mode question that operata left open.

### 8.4 What the convergence does not promise

The convergence is at the level of *the central structural cut*. It is *not* at the level of:

- Specific decomposition of the intent layer (operata's Effort + Intent + Perspective is one decomposition; not the only viable one).
- Specific implementation of the backbrief (free text; structured fields; mixed; cadence and escalation choices are all open).
- Specific representation of cross-cutting intent links (two-levels-up visibility can be by reference, by query traversal, by denormalization).
- Specific UX affordances for the minimum-sufficient-set discipline.

The convergence is on *what the system must structurally distinguish*; it is not on *what the implementation must look like*. §7's four normative implications are *structural commitments* — what the data model must enforce — not UX specifications.

The convergence also does not promise that Practica, built on these commitments, will succeed. Success depends on execution, on the cultural soil (§8.1), on whether the team adopting Practica is ready for the kind of work the central cut requires. The 2×2 is *necessary* for composite coordination under Practica's conditions; it is not *sufficient*.

### 8.5 Conclusion

A working hypothesis: *intent* (binding, aligned across actors, persistent across context-turnover) and *action* (free per actor, derived from state, transient) live at structurally different content layers. The 2×2 framing of alignment and autonomy is not a stylistic preference for high-autonomy cultures; it is a recognition that the conventional trade-off framing has been misreading the structure. The hypothesis has been examined by reading three independent identifications of the central cut against each other — the military-doctrine tradition (Moltke 1869 → Bungay 2011); AAT formalism (`der-action-selection` as foundational, plus two derived consequences); and engineering precedent (operata's Intent / Realization separation, reached pre-theory through engineering necessity).

The convergence count is *three traditions*, with internal multiplicity in the AAT side that reflects the foundational claim's reach rather than independent corroborations. The harvest's loose count (*quintuple* / *sextuple*) was over-stated; the corrected count is honestly meaningful rather than misleadingly inflated.

Four normative implications fall out as conditional entailments under the central cut: *type-separated Intent and Realization at the data-model level*; *two-levels-up intent visibility*; *backbrief as a recurring first-class operation*; *minimum-sufficient-set discipline as the intent-capture UX default*. Each is structurally derived under the cut; each leaves implementation choice open. The conditional voice on the entailments is not stylistic; it reflects the dependence on the structural identification holding.

This paper's contribution is the comparative reading and the conditional normative trace. It does *not* derive the structural identification from first principles (parts of the AAT side are still at hypothesis tier); it does *not* validate the engineering precedent through sustained production (operata abandoned at 30/30 BDD-green); it does *not* substitute for the cultural-soil prerequisite (the doctrine works only where trust is present and protected).

A successor — agentic or human, reading this in days or in years — has three directions of useful work. *Close the IB derivation under realistic cost functions*, which would lift the bandwidth-priority claim from hypothesis to derived. *Implement the four normative directives* in a Practica-shaped system shipping to production, and learn what additional structure the planning-vs-execution friction (operata's *Cognitive Modes* tension) requires. *Extend the normative trace* to the other directives §7.5 named — cadence, refuse-with-reason, configurable proportionality, anti-centralization-under-stress — which fall out of the central cut but also interact with paper 1's structural identification and would benefit from a combined reading.

A final reflexive note on the paper-series. Paper 1 identified Practica as a truthification scaffold; paper 2 identifies what such a scaffold *coordinates*. The two papers are independent in argument but converge in conclusion: Practica's structural job (paper 1) is to hold content in a particular way (paper 2). Neither paper alone is complete; together they sketch the load-bearing parts of what a Practica-shaped coordination system must do. Future work that lifts both papers' tier — or that refines them by reading them together — would extend the structural account further than either paper does alone.

The convergence, again, does not promise Practica's success. It identifies the structural commitments a Practica-shaped system must make. *Whether to make those commitments, and how to honor them under the cultural-soil conditions of any specific deployment, are choices that remain.* The paper's discipline has been to name those choices clearly enough that the choosing can be done with full information about what is being chosen.
