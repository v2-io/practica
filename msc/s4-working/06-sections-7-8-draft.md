# §7 + §8 — Honest limits and Conclusion (draft)

---

# 7 — Honest limits

The paper has presented a convergence claim and a conditional supersession structure. The voice has been calibrated throughout: tier marks where AAT has them, *conditional on the identification holding* where the supersession depends on it, prior-art acknowledgment where AAT's own segments make it explicit. This section names the limits more directly than the body sections have, so the reader can locate where the paper's argument stops and where future work would need to continue.

## 7.1 What the AAT side does not yet establish

The AAT segments cited are at *discussion-grade synthesis* tier. Specifically:

- `der-class-coercion-via-wrapping.md` is *derived under stated conditions* — the (C1)–(C3) admissibility conditions on the component. Theorem 1 (exact form) and Theorem 2 (approximate form with leakage bound) are proved under these conditions; the conditions themselves are not always operationally testable for a deployed LLM component, and Class C components (fundamentally goal-conditioned) are explicitly out of scope.
- `der-class-coercion-in-composition.md` is *derived under stated conditions* — the wrapper-design constraints (D-A2)–(D-A4) plus inheritance from the prerequisite directed-separation result. The Brooks's-Law tempo cost has a *qualitative* claim that is robust (the wrapper runs slower than the raw component, by a structurally determined factor) and a *quantitative* form whose specific constants would need verification at the relevant home segments.
- `form-composition-closure.md` is *conditional / formulation choice*: it sets up the closure-defect quantities and the bridge lemma under explicit admissibility constraints (A1)–(A4) and projection-admissibility (P1)–(P3). The tier-1 (Kalman, gradient on strongly convex losses, linear-PD positive-definite) case has a derived bridge-lemma result; tier-2 and tier-3 cases need additional verification per-domain.
- `der-orient-cascade.md` is at status `claims-verified` — higher than synthesis grade. *The cascade ordering itself is exact* (forced by information dependency). The *content* for steps 3-5 is at discussion-grade synthesis. What is *not* derived is the *timing* — how long to spend on each step before proceeding.
- `der-directed-separation.md` is at *robust qualitative* tier for the architectural classification. The Class 1 / 2 / 3 partition is structurally distinct and well-motivated by examples; the $\kappa_{\mathrm{processing}}$ operationalization is well-defined but not typically computable in closed form for real architectures.

The aggregation of these segments into the structural identification claimed in §3 is at a tier *no higher than the weakest input*. The paper's voice has reflected this: the structural identification is *named*, not *proved*. Tightening any of the home segments to higher tier would tighten the identification correspondingly; until then, the identification carries the synthesis-grade epistemic load.

## 7.2 What the engineering side does not establish

Two limits matter.

*Operata did not ship to sustained production.* The 30/30 BDD-green status at abandonment is non-trivial — the engineering contracts held under test. But sustained production use would have exposed integration failure modes, organizational adoption frictions, and edge cases that pre-production engineering does not surface. The engineering side is *convicted of the shape* at the architectural / data-model / contract level; it is not validated by sustained use. A successor implementation of Practica that ships to production and operates over months would supply evidence the current corpus cannot.

*The independence of the engineering instances is an empirical claim I have not verified.* §5.4 argued the convergence is meaningful because the AAT-side and engineering-side methods have disjoint failure modes. The argument depends on TodoWrite, LLMCompiler, and operata being genuinely independent design instances rather than being influenced by each other through the small LLM-agent design community. I have not done historian-of-engineering work to verify this independence. The convergence claim is *as strong as the historical-independence claim*. A reader who wants to scrutinize the convergence on those grounds is encouraged to investigate.

## 7.3 What the supersession structure does not derive

§6 traced three engineering consequences as *entailments under the structural identification*. The entailments are short and structural; I would think them hard to refute given the identification. But the supersession structure does not derive the engineering consequences from first principles. It traces them *from* the structural identification, *to* specific design requirements, *under* the conditions stated. If the identification is incomplete or wrong, the entailments do not survive.

A genuinely-derived supersession would require:

- The structural identification at theorem-grade tier (not synthesis-grade);
- An explicit definition of "Practica-shaped system" sufficient to determine whether a given system is in scope;
- A formal statement of the entailment from the structural identification to each engineering consequence, with stated conditions.

None of these are in this paper. The paper is *comparative-descriptive* in the title and *conditional-traceable* in the supersession section. Lifting any of these to a stronger argumentative footing is future work.

## 7.4 What the convergence does not promise

A final scoping marker. The convergence is at the level of *the structural job*. It tells us what shape Practica-as-a-system must have. It does *not* tell us:

- Whether building Practica is *worth* doing — the convergence does not address opportunity cost, alternatives, or domain fit.
- Whether Practica will *succeed* once built — the convergence describes the structural job; success depends on execution, organizational adoption, and the willingness of human collaborators to inhabit the role the structural job requires of them.
- Whether the AAT framework as a whole is *correct* — the paper has cited AAT segments at their stated tiers; the framework's broader claims are out of scope for the convergence argument.
- Whether the engineering instances cited are *the best examples* of the structural shape — they are *operationally visible* examples that are useful for the comparative reading. Other instances may be stronger; some may exist that disconfirm the convergence.

These are real limits, not rhetorical hedges. A reader who wants Practica to be built, or to evaluate whether it should be, will need evidence and arguments the convergence claim does not supply. The paper's contribution is the comparative reading and the conditional supersession structure — narrower than a full case for Practica, and acknowledged as such.

# 8 — Conclusion

A working hypothesis: Practica's structural identity is closer to a *truthification scaffold for serial sub-agents using Class 3 substrates* than to a familiar task tracker. The hypothesis has been examined here by reading two independent identifications of the structural shape against each other — AAT's formal wrapping construction (§3) and the LLM-agent engineering community's plumbing/intelligence-split pattern (§4) — and naming the four commitments (S1)–(S4) the two paths share (§5). The convergence is meaningful evidence because the two paths have disjoint failure modes; it is also limited evidence because both sides are at incomplete tiers (synthesis-grade for AAT; convicted-of-shape for engineering).

Under the structural identification, several engineering choices commonly presented as independent design decisions become *consequences* of the identification: bootstrap-recovery safety, soft-claiming over hard locking, day-one DAG-with-cycle-detection (§6). The consequences hold under stated conditions; the conditional structure has been preserved in the prose. If the identification is right, the consequences follow; if the identification is wrong, the consequences do not.

The work for a successor — whether agentic or human, whether reading this in days or in years — falls into three directions.

*Lift the identification to higher tier.* The AAT home segments cited at synthesis grade can be assembled into a unified statement at derived grade. Doing so would tighten the supersession from *conditional entailment* to *derived structure*.

*Test the convergence empirically.* A Practica-shaped system that ships to production and operates for months would supply evidence the engineering side currently lacks. Whether it succeeds or fails would refine the structural identification: success under the four commitments would strengthen the claim; failure despite honoring them would refine the claim's scope.

*Trace additional consequences.* The supersession structure here covers three engineering choices. Several more candidates were named in §6.4 — the four-resource decomposition, the single-in-progress concurrency limit, the propose-then-commit workflow. Tracing each as an entailment-under-the-identification, with conditions, would extend the structural account.

The convergence does not promise Practica's success. It identifies the structural job a Practica-shaped system must do, and traces a small number of design consequences as conditional entailments. If the identification is right, building Practica becomes the work of honoring the structural job under conditions specific to the deployment. If the identification is wrong, the work is different but the paper's comparative reading still holds — *what AAT and the LLM-agent engineering community independently reach for* is a fact about both communities, separate from whether the reaching is structurally correct.

A final reflexive note. The paper has been written under voice discipline that mirrors the structural job it describes. The substantive claims are *named* rather than *asserted*; the conditional structure is *preserved* rather than *softened away*; the prior art and limits are *visible* rather than *buried*. The discipline is not stylistic. It is what writing in the presence of a serial-sub-agent successor demands: anything overstated here becomes load-bearing for a next agent who inherits the work, and the next agent will be operating under context-turnover with no access to the deliberation that produced the claims. The conditional voice is *the form* the paper's content requires. Practica's structural job and the paper's structural job are, in this respect, the same.

---

*End §7 + §8 draft. Word count: ~2,000 combined. To iterate.*
