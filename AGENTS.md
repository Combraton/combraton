# Combraton — working instructions

Build the human-steered spatial control plane and desktop application. Own selected direction, workflow readiness, acceptance and branch adoption. Do not own PIO execution facts or CBR memory truth. Do not require PIO/CBR to run through this desktop, use private sibling imports, or share writable product stores.

## Read the right sources

Start with [README](README.md) and [the documentation map](docs/README.md), then [baseline](docs/architecture/BASELINE.md), [architecture](docs/architecture/ARCHITECTURE.md), [steering](docs/architecture/STEERING.md), and [UI](docs/architecture/UI.md). Read the [accepted baseline](docs/architecture/BASELINE.md) and relevant shared/domain sections for boundary changes. Follow [the shared development workflow](docs/DEVELOPMENT.md); record its commit/revision for multi-session work. Research and old code are references, not silent overrides of accepted decisions.

## Preserve these boundaries

- Executable workflow nodes are existing harnesses. Template stages group/configure workflows; they add neither fake nodes nor a canvas navigation level.
- Preserve semantic zoom across orchestra/project/session/workflow, equivalent alternate operations, retained history and explicit successor/reuse. Restart does not undo external effects.
- Routine investigation and repair continue within agreed scope. Hold only named consequential transitions whose conditions are unmet; direction/authority/reserved judgments stay human-controlled.
- Keep selected intent, observed execution, memory claims, applicability and human acceptance distinct. Mock states cannot stand in for observations.

## Work and coordination

Inspect the assigned issue/task, branch, head, worktree and uncommitted changes before editing. Preserve unrelated work. For a large task, persist a small plan with outcome, scope, acceptance, dependencies and next step in `docs/work/` or the linked issue; do not rely on chat alone. One owner per task; one isolated worktree per concurrent writer. Agree shared contracts before consumers diverge.

Use subagents when a bounded independent investigation or review will help; pass scope, relevant invariants, source revisions and expected evidence explicitly. Prefer read-only helpers. Parallel writers require separate worktrees and non-overlapping scope/resources. Collect and verify results. Use separate top-level sessions for independently owned component implementations; no recursive swarm or permanent model-to-repo assignment is required.

Changing authority, graph/region semantics, template/history behavior, persistence/reconciliation, protocol compatibility or the scene renderer requires reading the affected contracts and a bounded primary-source investigation. Record accepted choices and superseded sections in the owning [decision record](docs/decisions/README.md). Escalate a needed change of direction, authority or reserved judgment; routine scoped investigation and repair proceed automatically.

## Verify and hand off

Run `python3 scripts/check_docs.py` from the repository root for documentation changes; see [verification](docs/VERIFICATION.md). Product runtime/build/test commands do not exist yet: do not invent them or report product checks as passed. Add reproducible commands when implementation introduces them.

Future product validation must cover authority boundaries, history/restart and real end-to-end journeys. For UI changes, exercise navigation and keyboard/reduced-motion behavior with actual browser evidence; Loom remains a simulated reference.

Review the actual diff at recorded base/head. Before a session ends, persist commits/files, commands with exit status and evidence, unresolved facts, active resources and the next action in the task handoff. Treat old handoffs as historical observations; reconcile them with the checkout. Keep public records free of credentials and private transcripts.

Use existing native harnesses to ship v0.1. Combraton self-development is deferred until all four usable v0.1 releases. Do not install ECC/global hooks, select a model or relax runtime permissions merely because a reference suggests it.
