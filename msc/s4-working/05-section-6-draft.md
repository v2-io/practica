# §6 — Supersession structure (conditional) (draft)

*Three engineering consequences traced as conditional implications of the structural identification.*

---

If the structural identification of §3 and §4 holds — that is, if the four shared commitments (S1)–(S4) from §5 capture what a system like Practica must do structurally — then several engineering choices commonly presented as independent design decisions become *consequences* rather than separate choices. This section traces three: *bootstrap-recovery safety* (E1), *soft-claiming over hard locking* (E2), and *day-one DAG-with-cycle-detection rather than tree-with-later-migration* (E5).

The traces are not derivations from first principles. They are *entailments* — each consequence follows from the structural identification under stated conditions. Conditional voice is preserved throughout: the entailments hold *if* the identification holds. The structural identification itself is at AAT discussion-grade synthesis tier; the engineering side is convicted-of-shape, not validated-by-production. The supersession claim is therefore: *given the identification, the consequences follow under specific conditions named below.*

Why bother tracing the supersession if both endpoints are conditional? Because the conditional structure is itself informative. Engineering choices presented as *"good ideas one might want to consider"* are weaker than engineering choices presented as *"structural consequences of the system's identity."* The first invites independent debate per choice; the second invites debate on the identification, with the choices riding on the outcome of that debate. The supersession structure changes *what the argument is about* — and that change is useful even when both sides are conditional.

## 6.1 Bootstrap-recovery safety (E1)

**The engineering claim.** A coordination system whose components include serial LLM sub-agents must support recovery of its own state without requiring its own intelligence layer to be operational. The plumbing-layer state must be readable and restorable by external means (filesystem inspection, plain-text reading, manual editing if needed) when the intelligence layer is unavailable, broken, or actively misbehaving.

Operata named this requirement in its TODO[^bootstrap-named] and lived its violation (the prior session whose state was *"accidentally wiped"*). The principle is concrete: if a bug in operata prevents reading the task list, the developer cannot see what to fix; the system has destroyed its own recovery path.

**The entailment.** If commitment (S1) holds — the plumbing layer is structurally typed to enforce things the intelligence layer cannot self-enforce — then the plumbing layer is *the* artifact of structural continuity. When the intelligence layer fails (bug, context-turnover, intentional shutdown), the plumbing-layer state is the only artifact of the system's commitments. The plumbing layer is *what makes the structural separation real*; if it is not recoverable without the intelligence layer, then the structural separation is not robust to intelligence-layer failure.

Under context-turnover (the second condition from §2.3), intelligence-layer failure is the *expected* case, not an edge case: sub-agents end at the end of their sessions; the next sub-agent starts cold. The plumbing layer mediates the handoff. If it requires the prior sub-agent's runtime to be inspectable, the handoff fails by design. The recovery path must be *substrate-level* (filesystem, plain text, version control), not *application-level* (the running tool).

The entailment is structural: under (S1) + serial context-turnover, plumbing-layer durability is forced. It is not an optional safety feature.

**What this conditions on.** The entailment requires both (S1) and serial context-turnover. A composite of always-on parallel agents would not face the same failure mode at the same intensity (though it would still benefit from plumbing-layer durability; the conditioning makes the requirement *forced* under the additional context-turnover condition).

**What this does not specify.** The form of the durable state — what file format, what storage substrate, what schema — is not specified by the entailment. Operata used SQLite plus YAML; other systems could use append-only logs, content-addressed objects, git-tracked plain text. The entailment specifies *that the plumbing-layer state must be recoverable without the intelligence layer*; it does not specify *how*. The implementation has degrees of freedom; the structural requirement does not.

[^bootstrap-named]: `~/src/operata/TODO.md` §"Why not dogfood operata with operata yet?": *"If a bug in operata prevents you from reading your task list, you can't see what to fix. Need a stable/unstable separation."* The stable/unstable separation proposal — running development against an installed gem version rather than the live development code — is one specific instantiation of the entailment; the entailment itself is more general.

## 6.2 Soft-claiming over hard locking (E2)

**The engineering claim.** Concurrency-control in a coordination system whose actors include serial LLM sub-agents must use *soft claims* (status-based signaling of intent to work on something) rather than *hard locks* (mutual-exclusion mechanisms that require a holder to release).

Operata's glossary names soft-claiming explicitly: *"Status-based signal that an agent is working on something without hard locking"*[^soft-claiming-defined]. The operata-system design document describes the pattern in detail, citing CRDT-based coordination, blackboard architectures, and git's optimistic-locking-at-commit model as the family the choice belongs to.

**The entailment.** Under serial context-turnover, any locking mechanism that requires a holder to *release* the lock is structurally broken: the holder is a sub-agent that will end at the end of its session, *taking the lock with it*. The next sub-agent inherits a stale-locked state; the coordination structure has degraded.

Soft-claiming is the coordination form that does not depend on holder persistence. A status field (*"agent X is working on this"*) is a signal, not an exclusion. Other actors observing the signal can choose to coordinate, parallelize, or proceed regardless. The signal degrades gracefully when the holder vanishes: the next sub-agent sees the status, can verify the holder is no longer active (by external means — the agent identity is in a CHRONICA log, a system process table, a human observer's confirmation), and proceeds without needing to *release* anything formally.

Under (S1) — structural separation at the plumbing-layer type signature — the plumbing layer holds the status signal. Reading the signal is a goal-blind belief-update operation: the agent's epistemic update about *"what is currently being worked on"* takes the status field as evidence. If the signal were a hard lock (with a release-required semantics), the goal-blind belief-update would have a side-effect on the plumbing layer's exclusion state, violating (S1)'s type-signed separation.

Soft-claiming is therefore forced by the combination of (S1) plus serial context-turnover. It is not a stylistic preference for low-coordination cultures; it is structurally required under the identification.

**What this does not specify.** The mechanism of soft-claiming — how the status is represented, how stale signals are detected, what the conflict-resolution policy is when two agents claim the same item — is not specified by the entailment. Operata used a simple status field plus claimant identification; other systems could layer CRDT-based metadata, voting protocols, or human-in-the-loop arbitration. The entailment requires *signal-not-exclusion*; it does not require any specific signaling mechanism.

[^soft-claiming-defined]: `~/src/operata/docs/glossary.md`: *"Soft Claiming: Status-based signal that an agent is working on something without hard locking."* The principle is also discussed at length in `~/src/operata/docs/exp/2025-11-26-operata-system.md` §"Multi-agent coordination favors soft claiming."

## 6.3 Day-one DAG-with-cycle-detection (E5)

**The engineering claim.** A coordination system whose state-space includes effort dependencies should be implemented as a directed-acyclic-graph (DAG) with explicit cycle-detection from day one — not as a tree with planned later migration to DAG.

Operata's TODO names this directly: *"Current model uses single `parent_id` (tree), but docs say 'intents form a directed graph.' Cross-cutting work is awkward—an intent can only prepare/support ONE parent."*[^operata-tree-dag] A proposed `IntentEdge` join table with cycle-detection is sketched in the same document; it was not shipped before operata's abandonment. The migration was *recognized* and *unbuilt*.

**The entailment.** Two structural facts force the DAG-from-day-one choice.

*Structural fact 1: non-trivial coordination domains often have cross-cutting structure.* Many real efforts relate to multiple parent efforts simultaneously — *"fix security vulnerability"* may contribute to security, performance, and compliance goals; *"refactor authentication"* may prepare for several downstream features. A tree forces a choice of which parent to attach to, losing the cross-cutting structure where it exists. The claim is not that *all* coordination domains have cross-cutting structure (project breakdown structures and pure organizational hierarchies sometimes do not); the claim is that the *interesting* domains for Practica's deployment do, and a tree-only data model cannot represent it.

*Structural fact 2: tree-to-DAG is a structural migration, not a parametric one.* AAT distinguishes parametric adaptation (tuning parameters within a fixed model class) from structural adaptation (changing the model class itself). The latter is required when the parametric class cannot represent the problem; once required, the migration is qualitatively different from parameter-tuning. In engineering terms: tree-to-DAG changes the data model, breaks existing queries, requires schema migration, invalidates references. It is not a refactor; it is a model-class change.

Under (S1) — the plumbing layer enforces structural invariants the intelligence layer cannot self-enforce — the data-model class is *itself* a structural commitment. A tree-shaped model commits the plumbing layer to single-parent structure; the intelligence layer cannot construct cross-cutting links because the data model has no slot for them. If cross-cutting links are needed (per structural fact 1), they must be represented in the data model.

The two facts together: cross-cutting structure is required (fact 1); changing the data-model class is a structural migration (fact 2); structural migrations in deployed systems are exactly where engineering momentum dies (operata is the witness, having recognized the need and been abandoned mid-migration). The combination forces day-one DAG: pay the upfront cost of representing the cross-cutting structure when there is no deployed state to migrate, rather than pay the deferred cost of migrating once deployed state exists.

The cycle-detection requirement is similarly forced. A DAG without cycle-detection becomes a directed graph (DG); the structural commitment to acyclicity is *what makes the model class a DAG rather than a DG*. Without cycle-detection, the intelligence layer can construct cycles inadvertently (an intent supporting a parent that supports it, indirectly), and the structural invariant is unenforced. (S1) requires the plumbing layer to enforce; therefore cycle-detection must be in the plumbing layer from day one.

**What this does not specify.** The form of the DAG representation — adjacency list, join table, edge collection, graph database — is not specified. The cycle-detection algorithm — DFS with coloring, topological sort with cycle reporting, incremental SCC tracking — is not specified. The user-facing affordances for representing cross-cutting links — typed edges, weighted links, free-form `related-to` annotations — are not specified. The entailment requires *DAG with cycle-detection in the plumbing layer from day one*; the implementation has degrees of freedom.

[^operata-tree-dag]: `~/src/operata/TODO.md` §"Intent Graph: Tree → DAG Migration": full text including the proposed `IntentEdge` resource and the planning notes. *"Prerequisite: Archema M:M conventions [shared with Archema MAP.md]. Before migrating Intent to a graph, investigate and solidify Archema's support…"* The migration prerequisite chain explains, in operata's own words, why this kind of structural migration accumulates blocking dependencies and rarely ships once deployment has begun.

## 6.4 What the supersession structure does *not* establish

Three honest scoping markers.

**The three consequences are not exhaustive.** Other engineering choices may also follow from the structural identification — for example, the four-resource decomposition operata reached (Intent / Realization / Perspective / Effort) may be partially forced; the single-in-progress-at-a-time concurrency limit observable in TodoWrite may be forced under the bandwidth-floor analysis of AAT's persistence theorems; the propose-then-commit workflow common in LLM-agent systems may be forced under the directed-separation requirement. This paper traces three because they are operationally visible and have direct operata-side evidence. A fuller treatment would extend the trace.

**The consequences could be reached without the structural identification.** Bootstrap-recovery, soft-claiming, and day-one DAG are not novel engineering recommendations; they are familiar choices in well-engineered distributed systems. An engineer could reach them by experience without ever encountering the structural identification. The supersession claim is not *"only the structural identification leads to these choices"*; it is *"the structural identification renders these choices coherent as a set, traceable to a common origin, rather than as independent good ideas."* The change in argumentative structure is the work the supersession does.

**The supersession depends on the structural identification holding.** If the identification is wrong — if the four commitments (S1)–(S4) do not actually capture what a system like Practica must do — then the entailments do not survive. The conditional voice on the entailments is not stylistic; it reflects the dependence. The strength of the supersession claim is bounded above by the strength of the structural identification, which is at discussion-grade synthesis tier. Future work that lifts the identification to higher tier would correspondingly strengthen the supersession structure. Future work that refutes the identification — finds a working Practica-shaped system that does not satisfy (S1)–(S4) — would invalidate the entailments at the same stroke.[^supersession-strength]

[^supersession-strength]: A note on what I think the supersession structure actually achieves. I would think it is hard to refute that *if* (S1)–(S4) hold *then* E1, E2, E5 follow under the conditions stated — the entailments are short, named, and dependent on conditions I would accept independently. What is more genuinely open is *whether* (S1)–(S4) hold in full generality. The identification claim is what should be challenged, not the supersession structure under the claim. I have tried to keep this asymmetry visible in the prose: the supersession lines are entailment-shaped (conditional, structural); the identification is the load-bearing piece that future work should refine.

---

*End §6 draft. Word count: ~1,900. To iterate.*
