# §4 — The structural identification, engineering side (draft)

*Parallel section to §3. First draft. To iterate.*

---

The engineering side of the convergence is not one place. It is a family of LLM-agent design patterns recurring across systems whose components are LLMs. Three specific instances are useful to look at: Anthropic's *TodoWrite/TodoRead* pattern in Claude Code, the *LLMCompiler* plan-then-execute pattern (Kim et al., 2023), and *operata* — an abandoned-Dec-2025 Ruby task-tracking system whose internal documentation is where the principle gets explicitly named. Whether the three instances arose *independently* — meaning, without one influencing the others — is an empirical question this paper does not settle (see §4.6 and §7.2 for the honest scoping). What is verifiable is that the *shape* recurs across them: three systems with different lineages, different scopes, and different implementations exhibit a structurally similar separation. The recurrence is the engineering-side input to the convergence claim; the independence question scopes how strong the convergence evidence is.

The treatment here is asymmetric. *TodoWrite/TodoRead* and *LLMCompiler* are described briefly, as enacted instances visible from the outside; for both, the analysis I cite is operata's own observation of them, not a fresh primary-source claim about each system's design intent. *Operata* is described at more depth, because operata is the bridge: the engineering-side artifact that *names* the principle the other two *enact*. Operata also pays a debt the AAT side cannot — it tells us what specifically goes wrong when the structural job is left undone.

## 4.1 What the engineering side is reaching for

The pattern, as operata names it: separate *"what to do" (agent intelligence) from "when to do it" (CLI / scheduler determinism)*[^operata-system-principle]. The intelligence layer is where LLM judgment lives — answering open questions, choosing among alternatives, generating decompositions. The plumbing layer is where determinism lives — bookkeeping, state tracking, scheduling, format enforcement, persistence. The plumbing layer is *deliberately not LLM-driven*: it must be inspectable, reproducible, and operable without the intelligence layer running.

This is the same structural shape §3 introduced. Read against the AAT vocabulary:

- The plumbing layer is structurally typed to enforce things the intelligence layer cannot self-enforce — exactly the role the wrapping construction's $q_M$ and $f_M$ play in keeping the belief-update goal-blind.
- The plumbing/intelligence separation is *deliberate divergence* — the engineered system behaves differently from the raw LLM, because the plumbing imposes structure the raw LLM would not impose. This is the same $\varepsilon^*_{\text{coerce}}$ situation from §3.6: the divergence is wanted, not failed.
- The cost is paid in tempo — the plumbing layer adds steps per cycle that a raw LLM would not need. This is the engineering shadow of the Brooks's-Law inequality from §3.4.

The engineering analysis side rarely makes the cost/structural-shape relationship explicit in the form §3 presents. The convergence is at the level of shape, not at the level of analysis.

[^operata-system-principle]: `~/src/operata/docs/exp/2025-11-26-operata-system.md` §"LLM agent patterns reveal the plumbing/intelligence split": *"LLMCompiler's DAG pattern is particularly relevant: the planner generates a DAG of tasks with dependencies, and a Task Fetching Unit schedules execution based on those dependencies. This separates 'what to do' (agent intelligence) from 'when to do it' (CLI/scheduler determinism)."* Conclusion: *"From LLM agent patterns: CLI as deterministic plumbing layer (TodoWrite pattern), single in-progress task at a time, git as checkpoint/rollback system, propose-before-commit workflow for speculative decomposition."* Final paragraph: *"…all while collaborating with humans through an imperative CLI that maintains deterministic state management beneath the intelligence layer."*

## 4.2 The TodoWrite / TodoRead pattern

Claude Code's TodoWrite and TodoRead tools[^todowrite-note] are a no-op surface: they do not execute external logic. They maintain a list of todo items the agent has named, with status fields (`pending`, `in_progress`, `completed`), and they require explicit transitions between status states. The state-machine discipline — *"Mark as in_progress BEFORE beginning work. Only have one in_progress at a time"* — lives in the plumbing, not in the LLM[^todowrite-pattern].

Looking at this with the §3 vocabulary: TodoWrite is a partial-wrapping-shaped affordance for the *task-tracking* aspect of an LLM-agent's work. The plumbing maintains the status fields; the intelligence chooses what to put in them and what to do next. The agent cannot bypass the state machine (the plumbing enforces "one in_progress at a time" structurally); the agent retains discretion about what the work-items themselves are (the intelligence chooses what tasks to enumerate). The split between *what* and *when* is enforced at the tool boundary.

This is not analyzed in TodoWrite's documentation as a structural principle. It is what working practitioners discovered by building systems that need to keep agent-driven task lists coherent across long-running sessions.

[^todowrite-note]: TodoWrite/TodoRead are the task-tracking tools in Claude Code (Anthropic, 2024–2025), the same surface this paper's own task list (visible to the agent author at draft time) lives behind. I have direct familiarity with the surface but do not have primary documentation to cite beyond operata's characterization in [^operata-system-principle].

[^todowrite-pattern]: `~/src/operata/docs/exp/2025-11-26-operata-system.md` §"LLM agent patterns reveal the plumbing/intelligence split", on TodoWrite: *"Claude Code's TodoWrite/TodoRead pattern demonstrates the exact architecture you're describing: a no-op tool that structures agent thinking without executing external logic."* Status-machine discipline: *"Status state machine: pending → in_progress → completed with explicit transitions. Claude Code: 'Mark as in_progress BEFORE beginning work. Only have one in_progress at a time.'"*

## 4.3 LLMCompiler's plan-then-execute separation

LLMCompiler[^llmcompiler] generates a directed-acyclic-graph of subtasks via an LLM planner, then dispatches the graph to a *Task Fetching Unit* — a deterministic scheduler — which orchestrates execution. The structural separation is at the boundary between the planner and the scheduler:

- The planner is *intelligence* — it interprets the user's query and produces a DAG of subtasks with dependencies. This is where LLM judgment lives.
- The Task Fetching Unit is *plumbing* — it walks the DAG, dispatches subtasks when their dependencies resolve, handles parallelism. This is deterministic execution; no LLM judgment is invoked at this layer.

What the LLM produces (the DAG) is a *typed artifact*: a structure the scheduler can consume without further LLM reasoning. The plumbing's job is to make the DAG executable; the intelligence's job is to produce a DAG that captures the work.

Reading this against §3: the DAG is the type-signed boundary between intelligence and plumbing — analogous to the wrapper's structured $(M_W, G_W)$ state. The scheduler is structurally typed to consume DAG nodes, not LLM tokens. The intelligence layer cannot bypass the scheduler to *act*; the plumbing layer cannot bypass the intelligence to *plan*. Each layer is restricted to its structural function.

[^llmcompiler]: Kim, S. et al. (2023), *An LLM Compiler for Parallel Function Calling*, arXiv:2312.04511. I have not read the primary paper directly; the characterization above relies on operata's own analysis in [^operata-system-principle], which describes LLMCompiler's *Task Fetching Unit* and the planner/scheduler split. A careful reader who wants to verify the architecture should consult the primary source.

## 4.4 Operata: explicit naming and engineering crystallization

Operata (`~/src/operata/`) was a Ruby CLI task-tracking system built October–December 2025 by the same author as practica's foundation. It reached 30/30 passing BDD tests by abandonment[^operata-bdd] and named the plumbing/intelligence split as a structural principle in its internal documentation. Operata's pre-theory engineering is the closest available analogue to what §3's AAT analysis arrives at by formal derivation.

Two things matter about operata for the convergence claim.

**First: operata explicitly names the principle.** The `2025-11-26-operata-system.md` design document, written before the AAT formalism existed in its current form, names the plumbing/intelligence split as the structural principle behind several converging LLM-agent patterns operata had surveyed. The principle is not implicit in operata's code; it is stated:

> *"This separates 'what to do' (agent intelligence) from 'when to do it' (CLI/scheduler determinism)."*[^operata-system-principle]

> *"CLI as deterministic plumbing layer (TodoWrite pattern), single in-progress task at a time, git as checkpoint/rollback system, propose-before-commit workflow."*[^operata-system-principle]

**Second: operata reached a worked four-resource data model.** The Ruby implementation crystallized a specific decomposition[^operata-resources]:

| Resource | What it holds | What it does not hold |
|---|---|---|
| **Intent** | A desired state or outcome — *"what we want to achieve"* | Actions; ordering; execution-time concerns |
| **Realization** | What actually happened against an intent — outcome + delta-from-expected | Goals; planning content |
| **Perspective** | A per-actor focus — who is looking, what matters to them | Global ordering; ownership |
| **Effort** | A bounded initiative with origin, intent, temporal span | Tactical procedure; specific actions |

Two structural observations about this decomposition. *Intent and Realization are structurally separated by type signature*: an Intent record holds the desired state and the rationale; a Realization record holds *"what happened versus expected"* with no goal information. The decomposition enforces a goal-blind belief-update structure — Realizations are the substrate from which the system updates its model of reality, and they cannot, by data-model construction, encode goal-conditioned interpretations. This is *operationally analogous* to §3.2's $q_M$ type signature: the belief-update path cannot see $G_W$ because the data model structurally separates the two. *The analogy is at the level of structural function* — operata's data-model separation is not formally the same operation as $q_M$'s type signature, but both perform the same job (preventing goal information from entering the belief-update path) by different means (data-model construction vs. type-signed function argument). Operata reached this through engineering necessity (the cognitive-modes-tension working note in operata's TODO[^operata-cognitive-modes] names that storing actions in the intent graph creates friction; the resolution was Realization as a distinct resource).

*Perspective and Effort separate sovereign-per-actor concerns from project-scope concerns* — a different axis, useful for §6 but tangential to the structural-job claim being established here.

**Third: operata names a generalization of itself.** Operata's TODO explicitly identifies that operata serves *two distinct purposes* — a LOCUS-level coordination point (project-scoped, shared) and a Personal-level individual focus (private, sovereign across projects), and recommends they be *"independent systems with a sync layer, not a shared database"*[^operata-locus-personal]. This is a structural axis distinct from the plumbing/intelligence split, and it foreshadows practica's design space. It is also where operata stopped: the migration from tree-shaped Intent to DAG-with-cycle-detection was *recognized but not shipped*[^operata-dag].

[^operata-bdd]: `~/src/operata/TODO.md` §"Current State (2025-12-06)" and Cucumber/Aruba features: 30/30 passing BDD specs at abandonment. *"`features/` - Cucumber/Aruba BDD specs (30/30 passing)."*

[^operata-resources]: `~/src/operata/docs/glossary.md` §"Core Domain" — the four resources defined precisely. *"Effort: A bounded initiative with origin, intent, and temporal span. Intent: A desired state or outcome; the core unit of Operata. Unlike traditional 'tasks' which describe actions, intents describe states we want to achieve. This inversion enables back-planning. Realization: What actually happened when working on an intent. Captures the gap between expectation and reality, supporting the principle of preserving intent. Perspective: Contextual focus—who's looking and what matters to them."*

[^operata-cognitive-modes]: `~/src/operata/TODO.md` §"Cognitive Modes: Intent vs Action": *"Intent-oriented framing ('what states need to exist?') is excellent for planning and understanding dependencies. But execution requires a different cognitive mode ('what will I do next, in what order?'). Forcing execution into the intent graph creates friction."* The tension was identified; three proposed resolutions are listed; none were settled at abandonment.

[^operata-locus-personal]: Same source, §"Scope & Dual Nature": *"Operata serves two distinct but related purposes that will likely be **independent systems with a sync layer**, not a shared database. … Previous sessions conflated these as 'two views of one database' when they're actually two independent systems that sync. This explains ambiguity in: Perspective …; Effort ownership (`owner_id` vs `locus_id`); Storage model."*

[^operata-dag]: Same source, §"Intent Graph: Tree → DAG Migration": *"Current model uses single `parent_id` (tree), but docs say 'intents form a directed graph.' Cross-cutting work is awkward—an intent can only prepare/support ONE parent."* A proposed `IntentEdge` join table with cycle-detection was sketched; planned but not shipped before abandonment.

## 4.5 The lived texture: what operata died of

Operata's TODO contains a section explicitly named *"Why not dogfood operata with operata yet?"* It reads in full:

> *"If a bug in operata prevents you from reading your task list, you can't see what to fix. Need a stable/unstable separation."*[^operata-bootstrap]

This is engineering catastrophe naming itself in operata's own voice. The system *cannot use itself for development tracking* because a bug at the intelligence layer (or even at the plumbing layer) would deny the developer access to their own task list — including the task to fix the bug. The structural separation operata was trying to build is *also the separation that lets the developer recover when the system fails*. Operata recognized the requirement; operata did not solve it before abandonment.

Operata's own state was, in fact, wiped at one point. The TODO contains a *"Lost State (from prior session)"* section listing what was being tracked before the database was *"accidentally wiped"*[^operata-lost-state] — recovered from memory and notes, not from the system. The engineering catastrophe predicted by the *why-not-dogfood* note was experienced before abandonment.

This is not a side observation. The bootstrap-recovery requirement falls out of the structural identification §3 establishes: if the plumbing layer is what enforces structural separation the intelligence layer cannot self-enforce, then the plumbing layer must be readable and restorable when the intelligence layer is unavailable. *Otherwise, the system cannot recover from its own failure modes.* Operata named the requirement, lived the failure, and was abandoned before the requirement could be met.

The engineering teaches by failure here in a way the AAT analysis cannot. The AAT formalism establishes the structural job at the wrapper level; it does not, on its own, articulate why the *plumbing layer* must be more durable than the intelligence layer. Operata's lived constraint supplies the answer: under serial sub-agents whose intelligence-layer state does not persist across context-turnover, the plumbing layer is *the* artifact of continuity. If the plumbing fails, there is no continuity to recover.

[^operata-bootstrap]: Same source, §"Why not dogfood operata with operata yet?": full text as quoted. The construction immediately below: *"`ops` (gem install) - installed from known-working release, used for real tracking. `./exe/ops` - current worktree code for testing (run via bundle exec or directly)."* The proposed resolution is a stable/unstable separation — running development against an installed gem version, not the live code.

[^operata-lost-state]: Same source, §"Lost State (from prior session)": *"The following was being tracked in operata before database was accidentally wiped: Effort: 'Operata Development' … Earlier session also had: Effort: 'Operata MVP' …"* Recovered from memory and notes.

## 4.6 What the engineering side does not establish

Three honest scoping markers before §5 reads the AAT and engineering sides against each other.

**The convergence is observational, not experimental.** No experiment has been run that varies the structural job and measures the outcome. The engineering instances we have are *cases that converged on the structural shape*. We do not have negative cases (systems that deliberately rejected the structural separation and either succeeded despite it or failed because of it) controlled to isolate the structural variable. The convergence is evidence about what working systems look like; it is not evidence that other shapes cannot work.

**Operata did not ship to production.** The 30/30 BDD-green status is non-trivial — the engineering contract held — but the system was abandoned before sustained production use. Operata is engineering *convicted of the shape*: the architecture was committed, the contracts held under test, the design documents named the principle. It is not engineering *validated by production* in the sense one would want for an engineering claim. The lived texture from §4.5 is the closest available to production-validation, and it teaches by *failure mode* (E1, the bootstrap-recovery catastrophe) more than by success.

**The TodoWrite and LLMCompiler characterizations rely on operata's analysis, not on primary-source design intent.** I have direct familiarity with TodoWrite (it is the task-tracking surface I am using as this paper is drafted) but not with LLMCompiler beyond operata's description. A careful reader who wants to evaluate the engineering convergence at the level of *what these systems' designers intended* should consult those primary sources. The characterization here is what operata recorded having observed, plus my own light verification against TodoWrite's surface behavior.

These honest limits do not vacate the engineering side. They scope it. Three independent designs reach for a structurally similar separation; operata's documentation names the principle they share; operata's engineering teaches what happens when the principle is partially honored and then abandoned. The convergence is real at the level of *what working systems are shaped like* — it is also more limited than a triumphalist engineering-side framing would suggest, and the limits are worth carrying into §5.[^engineering-side-strength]

[^engineering-side-strength]: A note on what I think the engineering side actually establishes. The plumbing/intelligence split is something working LLM-agent practitioners *converge on without coordinating to do so*. That convergence happens despite the absence of a formal theory directing them is, I think, the load-bearing piece of evidence — and I would think it harder to refute than the surface text shows. The shape is not arbitrary; if it were, the convergence would not occur. But the convergence-without-coordination claim depends on whether the three instances I picked actually arose independently or whether each influenced the next through the small LLM-agent design community. The historical claim of independence is empirical and I have not verified it; I have stated only that operata's analysis explicitly names them as *observed* patterns rather than as *designed-with-each-other* patterns. A historian-of-engineering investigation could verify or refute the independence claim more strongly than this paper does.

---

*End §4 draft. Word count: ~2,100. To iterate.*
