# Practica — Structural & Process Invariants + Decisions (03-concrete)

**Status: SKELETON (2026-05-18) — not authored.** Sequenced after `02-normative` (which disciplines it by fixing *what practica is for* before *how it is built*). The lines below are intended scope, not content. FORMAT.md conventions apply (see `CLAUDE.md`).

## Intended scope

- **Structural invariants & architectural decisions.** The three-tier spec from `01-theory.md` §10 made into the codebase's module-classification discipline: every module is either theorem-forced (protected, minimal, cites the forcing segment), labeled convergent-choice (rejected alternatives recorded), or obviously-free — anything that is none of these is sprawl by definition. If the Python-exemplar path is taken (Joseph's open language decision; `CLAUDE.md`): the tier declaration is *structural and lint-enforced* (W₁), not review-hoped (W₂).
- **Process invariants & process decisions.** The build-time disciplines: W₁ belief-store/goal-store separation; low-ambiguity (verifiable, not judgmental) recorded state; guard *both* CM4 failure modes (fails-to-contract *and* never-was-a-composite); durable-$O_c$ protection ( `01-theory.md` §3–§6, §10).
- **The assumptions ledger (first-class).** The theory's *stated* assumptions (causal sufficiency, channel-independence, bounded-signaling, DA2′a-inc / Tier-1, stationarity, matched-channel) **plus** the *implicit* ones the real build enforces and surfaces. This is the channel where build-friction logs back as candidate theory assumptions — practica-the-build as the experiment that drives the theory. It is the concrete instrument for the stated concern that "we are almost certainly missing implicit assumptions the real world will enforce."
