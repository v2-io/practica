## 5 — The engineering identification (operata's Intent / Realization separation)

The engineering side of paper 2's convergence is operata's pre-theory data-model crystallization. The same operata that appears in paper 1 (as the named-precedent of the plumbing/intelligence split) here serves a different function: its core resource decomposition *enacted* the alignment-autonomy 2×2 by data-model construction, with the structural separation visible in the resource definitions themselves. Operata's documentation does not articulate the separation as "intent-binding-and-aligned versus action-free-and-autonomous" — the doctrinal vocabulary is not operata's. But the structural commitment is in the data model.

### 5.1 The two resources that matter for paper 2

Operata's domain model defines four resources — Effort, Intent, Realization, and Perspective[^operata-resources]. Two are load-bearing for paper 2: **Intent** and **Realization**.

> *Intent: A desired state or outcome; the core unit of Operata. Unlike traditional "tasks" which describe actions, intents describe states we want to achieve. This inversion enables back-planning.*
>
> *Realization: What actually happened when working on an intent. Captures the gap between expectation and reality, supporting the principle of preserving intent.*

The structural separation is in the type signatures. *Intent* holds a desired state — *what we want to achieve* — and is amenable to being held stably across actors and across time. *Realization* holds *what happened* — execution trace from one specific cycle, by definition per-actor and transient. *Intent* records do not carry execution traces. *Realization* records do not carry goal content. The data model enforces the separation.

The semantic content of each resource maps directly onto the alignment-autonomy 2×2 from §3:

- *Intent* is the **binding, aligned** content. It is shareable across actors. It can be aligned vertically (parent intents constrain child intents) and horizontally (peer intents around a shared higher-level intent). It is durable; the same intent can persist across many cycles and across many serial sub-agents.
- *Realization* is the **free, autonomous** content. Each actor's realization is per-actor; it is the record of what that actor did and what happened, not constraint on others. It is transient; realizations accumulate as the trace of execution, but no realization binds future actors.

This mapping is operationally tight. Operata's data model is the AAT-style state-not-action structure (§4.1) realized as a CRUD schema. It is also the Moltke/Bungay *intent binding / task free* structure realized as a CRUD schema. The mapping was reached *without operata explicitly engaging either tradition* — by the engineering pressure of building a system that needs to support back-planning (start from desired state; find what enables it) while also supporting honest reporting of what actually happened.

### 5.2 The "Cognitive Modes" tension: engineering meeting the structure honestly

A second piece of operata's documentation matters more than the first for paper 2's argument, because it shows operata *encountering* the structural separation through engineering necessity rather than recognizing it in advance. Operata's TODO contains an entry titled *Cognitive Modes: Intent vs Action*[^operata-cognitive-modes]:

> *"The tension: Intent-oriented framing ('what states need to exist?') is excellent for planning and understanding dependencies. But execution requires a different cognitive mode ('what will I do next, in what order?'). Forcing execution into the intent graph creates friction."*

Three proposed resolutions are listed; none were settled before operata's abandonment.

The substantive content for paper 2: operata *discovered* that the intent layer and the action layer are *cognitively distinct* through the friction of trying to make one layer carry both kinds of content. The intent-oriented framing was the right register for *planning* (back-planning, dependencies, what-needs-to-be-true); a different register was needed for *execution* (what-to-do-next, sequencing). The friction was not a UX problem solvable by polish; it was a structural fact about the kinds of content the system held.

This is exactly the failure mode the alignment-autonomy 2×2 names. Trying to hold intent and action at the same content layer creates the conflict that Moltke's *Befehl / Direktive* distinction resolved by separation. Operata met the structural fact through engineering pressure; the resolution operata reached toward — separate cognitive modes for separate content — is the same resolution Moltke and Bungay identified in different vocabulary.

The honest texture matters here. *Operata did not solve the friction.* It named the tension; it sketched three possible resolutions (a Session/Plan layer; a lightweight wrapper; an Intent `approach` field); it left the question open at abandonment. The engineering identification is *evidence that the structural separation is real* (a system that tried to ignore it hit measurable friction), but it is not evidence that operata had a refined design for handling the separation. The data-model separation between Intent and Realization is real and worked; the cognitive-mode separation between planning and execution remained an unresolved engineering problem.

### 5.3 What the engineering side establishes

A short summary before moving to §6.

The operata engineering identification establishes:

- That the *data-model separation* between desired-state and what-happened is reachable by engineering necessity, without needing either AAT's formal apparatus or military-doctrine vocabulary. Pre-theory crystallization is possible because the structural fact is real.
- That when a working system *attempts* to collapse intent and action into a single layer (e.g., by treating both as variants of "task"), it *encounters* friction — the *Cognitive Modes* working note is the friction recorded in operata's own voice. The friction is itself empirical evidence that the structural separation is not optional.
- That the data-model side is the *easier* of the two separations: holding Intent and Realization as type-separated resources is engineering-tractable. The harder separation — *cognitive-mode* separation between planning and execution — is unsolved by operata at abandonment and remains open.

What the engineering side *does not* establish:

- That operata's specific decomposition (Effort + Intent + Realization + Perspective) is the *right* decomposition. Other engineering choices are possible. What is established is that *some* type-separated decomposition is forced.
- That operata's design has been validated by sustained production. As noted in paper 1, operata was abandoned at 30/30 BDD-green; the engineering contracts held under test, but the system did not operate under sustained real-world use. *Convicted of the shape*, not *validated by production* — the same scoping as paper 1.[^engineering-scoping]

The convergence reading in §6 should weigh the engineering identification accordingly: real evidence of structural shape; bounded evidence of design correctness.

[^operata-resources]: `~/src/operata/docs/glossary.md` §"Core Domain": *"Effort: A bounded initiative with origin, intent, and temporal span. Intent: A desired state or outcome; the core unit of Operata. Unlike traditional 'tasks' which describe actions, intents describe states we want to achieve. This inversion enables back-planning. Realization: What actually happened when working on an intent. Captures the gap between expectation and reality, supporting the principle of preserving intent. Perspective: Contextual focus—who's looking and what matters to them."* The data-model separation between Intent and Realization is enforced at the resource definition level — Intent records do not carry execution traces; Realization records do not carry goal content.

[^operata-cognitive-modes]: `~/src/operata/TODO.md` §"Cognitive Modes: Intent vs Action": *"The tension: Intent-oriented framing ('what states need to exist?') is excellent for planning and understanding dependencies. But execution requires a different cognitive mode ('what will I do next, in what order?'). Forcing execution into the intent graph creates friction. … Three potential directions (to be discussed, chosen from, or integrated): 1. Session/Plan layer — First-class execution-order concept … 2. Lightweight wrapper — Session references intents but doesn't own them … 3. Intent `approach` field — Bridges the state→action gap."* Open at abandonment.

[^engineering-scoping]: Same convicted-of-shape / not-validated-by-production scoping as paper 1, §4.6 of `~/src/practica/msc/practica-structural-identity.md`. Operata's 30/30 BDD-green status at abandonment is non-trivial — the engineering contracts held under test — but sustained production use would have exposed integration failure modes and edge cases that pre-production engineering does not surface. The data-model separation between Intent and Realization is verified at the contract level; the broader design has not been validated by sustained use.
