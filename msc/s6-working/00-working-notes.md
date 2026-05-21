# docs/02-normative — distillation working notes (s6)

**Working substrate.** Iteration channel for the 02-normative directory. The durable artifacts live at `docs/02-normative.md` (index) plus `docs/02-normative/NN-cluster.md` (cluster files). This file is process-shaped; history → git; conclusions → the durable docs.

## Inputs

- **Harvest:** [[../02-normative-harvest]] — substrate with ~60 entries across H/M/U/O/P/CA/CV/SC/SS/E/S/E1-E9 clusters. The handoff (`[[../02-handoff-for-distillation]]`) gives the structural mental model and natural-clusters analysis.
- **Paper 1:** [[../practica-structural-identity]] — convergence on plumbing/intelligence split (M1+O2+E6 region). Provides the long-form argument for several architectural claims.
- **Paper 2:** [[../practica-intent-action-layers]] — convergence on alignment-autonomy 2×2 (S1+O1+U1 region). Provides the long-form argument for content-discipline claims.
- **Foundational reframe** (in the harvest): durable layer is *agency-granting conditions*, not content-transmission. Anchors several cross-cutting claims.

## Cluster cut (thematic, by kind-of-decision)

Six files in `docs/02-normative/`:

1. **`01-architectural-commitments.md`** — How the system must be structured.
   - Plumbing/intelligence split (paper 1).
   - Type-separated Intent and Realization resources (paper 2 N1).
   - LOCUS-vs-Personal axis as first-class architectural distinction (E3, [[../03-perspectives]]).
   - DAG-with-cycle-detection from day one (E5, paper 1 §6.3).
   - State-not-action spine — no stored action-queue / task-list / session-log resource (E4, paper 2 §4.1).
   - Four-resource baseline (Intent / Realization / Perspective / Effort) inherited from operata with explicit sharpening (E7).

2. **`02-coordination-affordances.md`** — How actors interact through the system.
   - Soft-claiming over hard locking (E2, paper 1 §6.2).
   - Two-levels-up intent visibility (paper 2 N2).
   - Backbrief as recurring first-class operation (paper 2 N3).
   - Anti-goals as first-class intent content distinct from constraints (S11).
   - Refuse-with-reason as first-class operation (Bungay Ch 3 "independent thinking obedience").
   - Configurable proportionality of strategy / execution / tactics levels by team domain (Bungay Ch 7 Fig 22).

3. **`03-content-discipline.md`** — What the system holds and how.
   - Minimum-sufficient-set discipline as UX default (paper 2 N4).
   - 70%-right intent commits — completeness not gated (Bungay Ch 3).
   - Three-level vocabulary: Strategy / Execution / Tactics (S10).
   - Command-vs-control architectural separation (S9 — intent layer never auto-completed from metrics).
   - COG as recurring site of attending, not stored content (S8); drift between articulations is information.
   - Six-section briefing template as canonical intent shape (S6, Bungay Appendix).

4. **`04-diagnostic-surfaces.md`** — What the system reveals.
   - Per-direction monitoring; aggregate metrics hide directional failures (P2).
   - Composite-scope observation as separate from per-sub-agent observation (M3, LIA1).
   - Trust as three-source decomposition: channel / source-competence / alignment (U3); calibration as Bayesian process (U4).
   - Four-regime event taxonomy: informative update / magnitude shock / structural shock / ambient noise (CV2).
   - Signed coupling per relationship — cooperative vs adversarial as single inequality read in opposite directions (CV1).
   - Per-actor regime classification (Regime A/B/C) for causal-identification strength (LIA2).

5. **`05-failure-mode-defaults.md`** — What the system structurally resists.
   - Bootstrap-recovery-safety — plumbing layer must be readable/restorable without intelligence layer (E1, paper 1 §6.1).
   - Force re-examination of long-confident efforts (triple-grounded: H1 stability-induced myopia + O3 Lyapunov-survival + SC4 adversarial-targeting).
   - "Failure to act is worse than mistake of means" as defaults principle (S4, 1888 Field Service Regulations).
   - Resist the toxic-cycle triple — no data-lake / dashboard sprawl, no task-template proliferation, no input-metric scoreboards as defaults (S2).
   - Anti-centralization-under-stress — over-specification is hardest exactly when it feels most needed (Bungay Ch 3, Hitler-as-failure-mode).
   - DAG-depth fragility warning — depth-monotone risk visible at design time (H4+SS4+E5 triple-grounded).

6. **`06-limits-and-positioning.md`** — What it does not promise.
   - Representability vs optimality (M4) — well-structured composite ≠ best composite for the work.
   - Moral-hazard / form-vs-content (S13) — the apparatus is ethically neutral; form alone is insufficient. Sharpens the protection-strategy positioning.
   - Cultural-soil constraint (Bungay Ch 3) — practica is amplification, not transformation; bounded above by team's existing trust and tolerance for honest mistakes.
   - Sandbox-to-deployment transport limit (CA3) — pre-deployment evaluation has structural limits.
   - Modular-safety-fails-under-goal-divergence (SC2) — "guard module" architectures are not structural guarantees.
   - Five productive tensions as 03's assumptions-ledger entries (E8) — Completeness ↔ Simplicity, Structure ↔ Emergence, History ↔ Clarity, Visibility ↔ Overload, Freedom ↔ Coordination.

## Form per cluster file

Each cluster file follows the same shape:

- **Theme** (one paragraph) — what kind of decision this cluster shapes.
- **The claims** — 3–6 normative claims, each:
  - **Title** in the form "Practica should X" or "X is forced by Y".
  - **One-paragraph statement** of the claim.
  - **Structural reasoning** — why the claim follows from theory / engineering / both.
  - **Tier marker** — exact / claims-verified / discussion-grade / convergent / engineering-grounded.
  - **Citation** in markdown footnote with local file path and supporting quote.
  - **Cross-references** to related claims in other cluster files (use `[[..]]` wikilinks).
- **What this cluster does not specify** — brief honest scoping at the end.

## Voice

Same calibrated discipline as papers 1 and 2:
- Tier markers visible.
- Conditional voice on bridge-inferences ("this would mean X" / "if Y holds, then X is forced").
- Strength-flags in footnotes where the claim is firmer than surface text shows.
- Citations have local file links and supporting quotes.
- No fourth-wall breaks — no references to the harvest's prior framings, no "we used to claim Y but now..." moves. Present-truth-durable-artifact discipline.

## Open questions to resolve as I draft

1. **Cross-cluster overlap.** Several claims belong to more than one cluster (e.g., E5 day-one DAG is both architectural and a failure-mode default; backbrief is both coordination and content-discipline). *Disposition:* assign each claim to its strongest home and cross-reference rather than duplicate.

2. **How much to summarize papers 1 and 2 versus reference them.** Each cluster file will cite paper 1 or paper 2 multiple times. *Disposition:* state the normative claim and cite the paper for the convergence argument. Don't re-argue the convergence; do state the claim with enough context to be useful standalone.

3. **The foundational reframe** (durable layer = agency-granting conditions, not content-transmission). It anchors several claims across multiple clusters. *Disposition:* introduce it in the index (`02-normative.md`) as the cross-cutting frame; cluster files reference it as needed.

4. **Tier-marking discipline.** AAT segments have stated tiers (exact / claims-verified / hypothesis / discussion-grade / etc.). For engineering-grounded claims (operata, etc.), the tier is "engineering-grounded" with provenance. For convergent claims (multiple traditions), the convergence is itself the evidence and the tier reflects the weakest input. *Disposition:* explicit tier on every claim; convergent claims explicitly named as such with the source traditions listed.

5. **Index design.** Should the index `02-normative.md` carry the *list of all claims with one-line summaries* (a quick-reference table), or just point into the cluster files? *Disposition:* both — the index has the quick-reference table plus the cluster overview plus pointers to the papers.

## Process

- **This iteration:** working notes (you are reading them); the index `02-normative.md` (replacing the current stub); one precedent cluster file `01-architectural-commitments.md`.
- **Next iteration:** the remaining five cluster files (probably one or two per iteration).
- **Then:** adversarial pass + Truth/Honesty judgment + cross-reference verification.

## Methodological lessons carried forward

From paper 1 → paper 2:
- Read sources in parallel at the start.
- Write durable files with proper heading levels for trivial assembly.
- Trust per-chapter working papers / prior verifications where the prior agent's fidelity is verifiable.
- Convergence-count honesty (paper 2 §6.3 lesson).

From paper 2 → here (after Joseph's clarification on fourth-wall breaks):
- *Don't correct claims the reader hasn't seen.* The durable artifact states present truth. References to prior framings only belong in the artifact if the reader will have encountered those framings.
- Present-tense disclosure is fine (e.g., "I have familiarity with X"); past-tense correction of un-stated claims is not.
- Backstage cycle-cleanup goes in working notes (or in successor annotations on the working substrate itself), not in the durable artifact.

These should make the 02 cluster files cleaner than paper 2's first draft.
