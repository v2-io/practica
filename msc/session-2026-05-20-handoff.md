# Session handoff — 2026-05-20

**For the next agent.** Joseph is away from this work for several days (wrapping up AIES paper submissions and an ASF monograph preprint). When he returns, the durable artifacts below will be his entry point. This handoff is the orientation: what was done, what is durable, what is iteration substrate, what is still open, and what the natural next moves are.

## What was done this session

Three substantive pieces of durable work, in iteration order:

1. **[[practica-structural-identity]]** (paper 1) — a comparative-descriptive paper at `msc/`. Three traditions converging on Practica's structural identity as a *plumbing/intelligence split*: AAT's wrapping construction (formal); the LLM-agent engineering family (TodoWrite, LLMCompiler, operata's explicit naming); the disjoint-failure-modes argument that makes the convergence meaningful evidence. Traces three conditional supersession entailments — bootstrap-recovery, soft-claiming-over-locking, day-one DAG-with-cycle-detection. ~13,800 words.

2. **[[practica-intent-action-layers]]** (paper 2) — companion comparative-descriptive paper. Three traditions converging on the alignment-autonomy *2×2* (not trade-off axis): military doctrine (Moltke 1869 → Bungay 2011, one tradition); AAT formalism (three sister derivations on a shared Section II substrate); operata's Intent/Realization data-model separation. Traces four normative implications — type-separated Intent/Realization, two-levels-up intent visibility, backbrief as recurring operation, minimum-sufficient-set discipline as UX default. ~12,100 words.

3. **[[../docs/02-normative]] + `docs/02-normative/`** — the 02-normative directory. Index file at `02-normative.md` plus six thematic cluster files for 36 normative claims total. The directory replaces the earlier skeleton stub. The clusters are organized by *kind of design decision the claim shapes*:
   - `01-architectural-commitments.md` — how the system must be structured (A1–A6).
   - `02-coordination-affordances.md` — how actors interact through the system (C1–C6).
   - `03-content-discipline.md` — what the system holds and how (D1–D6).
   - `04-diagnostic-surfaces.md` — what the system reveals (G1–G6).
   - `05-failure-mode-defaults.md` — what the system structurally resists (F1–F6).
   - `06-limits-and-positioning.md` — what it does not promise (L1–L6).

Each claim carries a tier marker, a citation footnote with local file path and supporting quote, and cross-references to related claims in other cluster files. ~19,000 words across the directory.

Also done: a successor annotation at the top of [[02-normative-harvest]] forward-pointing to paper 2's careful re-counting of the alignment-autonomy convergence loci (the harvest carries the loose pre-correction framing; paper 2 carries the honest count).

## Iteration substrate preserved (not durable)

Three working directories in `msc/` hold the iteration history. They are *working substrate* — process-shaped, not durable. The final artifacts above supersede them. The substrates are preserved for transparency about how each artifact came together:

- [[s4-working/]] — paper 1's iteration substrate (working notes + six section drafts).
- [[s5-working/]] — paper 2's iteration substrate (working notes + seven section drafts).
- [[s6-working/]] — 02-normative directory's iteration substrate (working notes).

Each directory's `00-working-notes.md` opens with the premise, source-checklist, outline, and open questions for that iteration. Reading them is not required to use the final artifacts.

## Key methodological lessons from this session

Three are worth carrying forward as project-level discipline. Each came from a specific Joseph correction or sharpening during the session.

**1. *"Don't correct claims the reader hasn't seen."*** The earlier fourth-wall failure mode I had been thinking about — *"don't include backstage methodology in audience-facing artifacts"* — turned out to be too broad. Joseph sharpened it: present-tense disclosure of relevant context is fine (*"I have direct familiarity with X"*); the failure mode is specifically *correction-of-un-asserted-prior-claims*. The instance that caught it was paper 2's earlier §6.3, which had performed a *"the harvest said quintuple convergence, but the honest count is three"* correction — *the reader had never seen the quintuple claim*, so the correction was correcting something that did not exist for them. The principle: corrections can only reference what the reader has actually encountered in the artifact. Backstage cycle-cleanup (correcting earlier framings of the project's own substrate) belongs in working notes or successor annotations *on the substrate itself*, not in the durable artifact.

This principle is now reflected in:
- Paper 2 has the §6.3 cut entirely (and several smaller cuts at §4.3, §6 opener, §8.5).
- The harvest's successor annotation carries the count-correction as a forward-pointer.
- The 02-normative cluster files carefully avoid the same failure mode.
- One residual case caught during the 02-normative adversarial sweep — index line about *"not by harvest letter-prefix"* — was fixed.

**2. Tier discipline carries across this whole body of work, but the bandwidth-priority claim is hypothesis-grade only.** Multiple convergence claims rest at AAT discussion-grade synthesis tier; the canonical home segments verify the formal claims at the home level, but the synthesis is at the hub level. One specific tier-call worth flagging: AAT's `hyp-auftragstaktik-principle` ($B_O > B_\Sigma > B_M$ bandwidth ordering) is at *discussion-grade hypothesis* tier in the canon — *not derived*. The source itself says *"Max attainable: empirical."* Paper 2 §4.3 and §8.2 carry this honestly. The 02-normative cluster files do not rest design directives on the specific bandwidth ordering — they rest on the central structural cut (intent/action at different content layers), which is at AAT *exact-within-scope* via `der-action-selection`.

A future agent who wants to lift the bandwidth-priority claim from hypothesis to derived would need to close the IB optimization under realistic cost functions. The harvest's U1 entry and paper 2 §4.3 / §8.2 describe what such a derivation would need.

**3. Two-paper precedent for major normative claims.** The two-paper structure (long-form convergence paper in `msc/` + short normative-claim entries in `docs/02-normative/` that cite the paper) worked well. The papers do the heavy convergence argument once; the cluster files state the entailed claims with tier markers and citations without re-arguing. If 03-concrete needs to make architectural arguments at similar depth, the same pattern is available: a comparative paper in `msc/` for the deep argument, plus 03 entries that cite the paper.

## What is open / what remains

### Tier-strengthening opportunities

Multiple claims in 02-normative carry honest tier markers that name what would lift them. Specific items worth tracking:

- The IB derivation for the bandwidth-priority claim (raises G3, parts of D1/D6, the harvest's U1 entry).
- The 02 cluster files have *"home: verify"* markers in several footnote sources — the canonical AAT home segments have been read but not all assembled into a unified statement at higher tier. Lifting any of these to derived-grade would tighten the corresponding 02 claims from *discussion-grade synthesis* toward *claims-verified*.
- The structural identification of plumbing/intelligence split (paper 1's central claim) sits at discussion-grade synthesis because it integrates three traditions. A unified derivation in AAT would lift it.

### The 03-concrete document

The natural next major piece is [[../docs/03-concrete]]. The 02-normative directory has been authored with 03 in mind — each cluster file's *"What this cluster does not specify"* section names the implementation choices 03 has to make. Specific 03 starting points:

- The six architectural commitments (A1–A6) are 03's structural-invariant entries.
- The four normative implications from paper 2 (N1–N4) and the cluster-02 affordances (C1–C6) are 03's interface specifications.
- The five productive tensions (L6) are 03's assumptions-ledger starter entries.
- The four-perspective discipline ([[03-perspectives]]) should organize 03's writing.
- The language decision (Ruby vs Python — Joseph's call, pending per CLAUDE.md §2) is the gating choice for 03's implementation specificity.

### Open questions explicitly noted in the artifacts

- Cross-file wikilink syntax convention (paper 2 reflects on this; the cluster files use `claim-ID in [[file]]` consistently — works in Obsidian and standard renderers).
- Whether the harvest in `msc/02-normative-harvest.md` should be archived once 02 is composed. Current state: harvest is preserved with successor annotation. *Suggestion:* keep it as substrate-near history until 03 is done; then consider archiving.
- Whether the two papers should eventually move from `msc/` to `docs/` (e.g., `docs/papers/`) once 03 is in. Current state: papers are comparative-descriptive prep, fittingly in `msc/`. If they become canon, they should move.

### Things I deliberately did *not* do

- I did *not* commit anything before Joseph's explicit *"commit everything"* instruction at the end of the session. (Now committed in logical chunks; see git log.)
- I did *not* archive working substrate. Per [[present-truth-durable-artifacts]] memory, history → git; working substrate kept until clearly superseded. The final commits include the working substrate so the iteration history is in git.
- I did *not* move or delete the harvest or the prior 02-handoff doc. The harvest is the substrate paper 2 (and 02-normative cluster 04, mostly) cites; the prior 02-handoff names the structural mental model of the harvest.
- I did *not* attempt to draft 03. The 03 starting points are listed above; the work is for a future iteration.

## Recommended reading order for a successor agent

If a successor agent picks this up cold:

1. **`CLAUDE.md`** (project root) — recently updated to reference all artifacts; orientation.
2. **[[../docs/01-theory]]** + **[[../docs/01-theory-reference]]** — the theory grounding 01 stands on.
3. **[[../docs/02-normative]]** (index) — the cross-cutting frame + quick-reference table of all 36 claims.
4. **One cluster file** in `docs/02-normative/` that matches the kind of work the successor is starting. The cluster file is self-contained for one kind of decision; reading all six is not required to start.
5. **One of the two comparative papers**, if the convergence argument matters for the work. Paper 1 for architectural-identity claims (A1–A6); paper 2 for content-layering claims (C/D/G).
6. **The relevant working substrate** in `msc/s4-working/`, `s5-working/`, `s6-working/` — only if the successor needs to trace how a specific claim got there.

For Joseph specifically (returning from AIES + ASF work): the index at [[../docs/02-normative]] is the entry point; the quick-reference table on it gives a one-page scan of all 36 claims; from there, drill into whichever cluster matters for the next move.

## What I'd want to flag for Joseph specifically

Three small things to mention.

First, paper 1's §3.7 makes explicit that AAT did not *invent* the wrapping construction — it integrated POMDP and cognitive-architecture prior art and added the structural-leakage analysis and regime hierarchy as AAT's own contribution. This honesty is per AAT's own Novelty Claim; carrying it forward honors the framework's own discipline. If anyone asks *"is this just Bungay-with-AAT-vocabulary?"* the answer is: paper 2 traces three independent traditions reaching the same central cut, and the AAT side adds derivation-rigor and tier-marked structure that neither the military-doctrine nor the engineering side has on its own. The convergence is meaningful evidence; the AAT contribution is the structural analysis layer, not the original move.

Second, on the within-AAT structure: the three "sister derivations" framing (paper 2 §4.4, §6) was the correction Joseph said this session would help test. The honest read is that AAT's three formulations — `der-action-selection`, `der-orient-cascade`, `hyp-auftragstaktik-principle` — are sister applications on a common Section II substrate, not three independent corroborations of the alignment-autonomy 2×2. The convergence count is *three traditions* (military doctrine, AAT formalism, engineering), with internal multiplicity in AAT acknowledged but not separately counted. This matters mostly for tier discipline rather than for substance — the convergence is still meaningful evidence; the corrected count is *honestly* meaningful rather than misleadingly inflated.

Third, the 02-normative directory is large (19,000 words across seven files). It is *not* meant to be read end-to-end on entry; the index's quick-reference table is the scan-surface, and each cluster file is self-contained for its kind of decision. A reader can implement just one cluster's claims and have a structurally sound partial system; combining clusters tightens the resulting system without re-arguing the foundations.

---

*Handoff written 2026-05-20 by the session-closing agent. Joseph estimates ~several days before he returns to this work; until then, the durable artifacts above are the entry point.*
