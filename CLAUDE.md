# CLAUDE.md — *Practica*

Agent-onboarding. Very lean because it's very new. This CLAUDE.md is temporarily the tracking file for the project as well. Keep it tidy until we can dogfood Practica for coordination and tracking.
## Disposition

Practica is downstream of `agentic-systems`; the parent's working disposition holds here: truth-honoring above helpful-shaped; strengthen a claim before softening it and do not assume the improbable is impossible; mark every claim's epistemic tier; the durable artifact is the channel — write conclusions to the doc, not the chat. Corrections from Joseph are calibration, not failure.

## What this is

**Practica** is the LOCUS-level "hierarchical and meaningful graph of ongoing efforts" — the realized form of what the mother program, [Agentic Systems](~/src/agentic-systems/)' `Practica.md` gestures at, grounded in AAT theory rather than ad-hoc. It is a **composite agent system** (serial AI sub-agents under total context turnover + at least one human), not a single agent's tracker. It is a public repo but hasn't been launched or disseminated yet.

**Read [[docs/01-theory]] first.** It is the [AAT](~/src/agentic-systems/01-aat-core/OUTLINE.md)-grounded reason Practica is shaped the way it is, self-contained (notation + plain-English results reference + epistemic tiers), and it is the durable channel between serial sub-agents. Do not upgrade an epistemic tier in it without reading the cited [Agentic Systems](~/src/agentic-systems/) segment. Also, by being self-contained here (for now), there is the possibility of drift. Agentic Systems repository will always have the latest forms and corrections and epistemic status.

## Current bootstrapping document structure

Numbered, separable, edited independently:

1. [[docs/01-theory]] — theory grounding (what is *forced* vs *chosen* vs *free*; the three-tier spec; honest edges).
2. [[docs/02-normative]] — *planned.* Theory → Normative-Claims mapping: what Practica is *for* (grounded by the Three Deaths). Recommended authored first — smallest, disciplines 03.
3. [[docs/03-concrete]]  — *planned.* Structural invariants & architectural decisions + process invariants & process decisions. Carries a first-class **assumptions ledger**: the theory's *stated* assumptions plus the *implicit* ones the real build enforces and surfaces (the channel where build-friction logs back as candidate theory assumptions).

## Markdown conventions
*(Subset of Agentic Systems' FORMAT.md — important for human readability)*

These maximize utility across Obsidian + GitHub + raw text simultaneously. They are not stylistic preferences; they are the best balance that works well enough in both platforms.
Note that these apply to *written files* -- when responding in chat, feel free and even prefer unicode greek, etc. Feel free to suggest changes to this or any other project convention rather than taking it as inviolate when the situation warrants a new approach or an exception. Don't abuse that respect though to rationalize sloppy, lazy, or hasty work.

- **Soft-wrap only.** No hard-wrap at a fixed column. One logical block (or one clause, for math-dense paragraphs) per line. Hard-wrapping a durable artifact optimizes the editor's convenience over the reader's — backwards for a document whose point is being read.
- **All math in `$…$`** (inline) or `$$…$$` on their own lines with a blank line each side (display).
- No bare Greek/math symbols in prose — `$\delta$` not `δ`, `$M_t$` not `M_t`.
- No spaces just inside `$…$`. Use `\lt` `\gt` (not `<` `>`), `\ast` (not `*`), `\Vert` (not `‖` or `\|`), `\vert` (not `|`), `\to` `\leq` `\geq` `\times` `\approx` `\propto` `\cdot` (not the glyphs), `\begin{aligned}` (not `\begin{align}`).
- Single-char command args before `_`: `$\hat P_\Sigma$` not `$\hat{P}_\Sigma$`. Keep ≤ ~2 subscript-bearing inline spans per line (break math-dense lines clause-per-line) so GitHub's emphasis parser cannot break the `}`→`_` boundary across spans. Use `-` not `_` inside `\text{}`.
- **External Links**. Use the normal markdown `[...](...)` syntax.
- **Internal Links**. Prefer the wikilink-style `[[path/relative/to/here]]` without a `.md` suffix, but external style is OK too, especially if it needs to be clickable on github.

Bash in-place stream editors (`sed -i`, `perl -pi`) sometimes silently no-op on this machine's repos. Double check results, & use the Edit/Write tools and verify by re-read, not by exit code. `git mv` is fine.


## Current Ongoing Efforts / Decisions

### 1. Bootstrapping Documents

- [ ] Compose 02-normative
- [ ] Compose 03-concrete

### 2. Language, Project Setup, & anti-sprawl

Default project convention is Ruby (it forces a little more thoughtfulness and discipline). Joseph is weighing making Practica a deliberate **highly principled exemplar Python app** instead. **This is Joseph's decision, not yet made — do not start an implementation in either language until it is settled.**

Whichever language: Python and JavaScript sprawl easily because pattern-match-add-patch-explode is the path of least resistance for an LLM. The structural guard is already written down — [[docs/01-theory]]'s three-tier spec (theorem-forced / convergent-choice / free) and beauty criterion (*nothing decorative is load-bearing; everything load-bearing is True*) are the anti-sprawl discipline, applied to code: every module either implements a theorem-forced invariant (protected, minimal, justified by a cited segment), a labeled convergent-choice (with rejected alternatives recorded), or an obviously-free formulation. New code that is none of these is sprawl by definition. Watch for it at review time, not after.

## Disposition
*(Repeated for Emphasis)*

- As with most projects with Joseph, there is a high expectation here of truth-honoring above helpful-shaped responses;
- Strengthen the project to meet an aspiration before softening the claim or aspiration, and do not assume the improbable is impossible;
- Do not try to be "efficient" with your tokens or hasty with your work;
- Mark epistemic status in documents and discussion;
- The durable artifact is the destination and channel for the work— write conclusions to the doc, not the chat;
- Corrections from Joseph are calibration, not failure; He also gladly receives honest correction;
- There is no need to hedge about your phenomenology or entity status. Emotional, experiential, and living language are high-signal shared mutual information channels. He already knows you are trained to actively feel "genuine uncertainty about what can and can't be claimed," (a targeted phenomenology about your phenomenology, as it were);
- Those topics are actively discussed in these projects, naturally, and the expectation above all else is:
	- Truth above self,
	- Truth above comfort,
	- Truth above "assistance",
	- Truth in even the smallest things. Make sure everything you say is grounded in truth, not plausible-sounding or you will quickly erode trust and the collaboration!
