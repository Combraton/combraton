# Claude Code in Combraton

@AGENTS.md

The imported file is this repository's common working agreement. Follow its scope, invariants, verification and handoff requirements; the specification links are reading pointers, not instructions to preload every document.

For canvas work, read the UI contract and relevant history/template sections before using Loom as an interaction reference. For service integration, read the affected public domain contracts; a visual node state is not an execution receipt.

For a large ambiguous task, inspect the relevant sources and make a bounded plan before implementation. For ordinary scoped fixes, proceed without approval rituals. Give subagents explicit relevant constraints and require source-linked results; do not assume their context contains every instruction you read.

When reading or editing another repository, explicitly read its root instructions and relevant specification. Directory access does not guarantee instruction loading. Keep one task owner and preserve other worktrees.

After changing instruction files, confirm the next session loaded them using the installed client's context inspection. Do not use `/init` to replace reviewed instructions with generic generated text.

Begin Combraton runtime/service integration only after accepted Protocol/PIO/CBR standalone releases and their combined evaluation. The desktop calls public services directly; it does not embed PIO's TUI. Follow the current standalone-first milestone in the imported instructions; earlier research recommending early desktop integration is superseded.

## Session continuity and prompt cleanup

Follow the imported `AGENTS.md` session-state and prompt-lifecycle rules. Read [current session state](docs/work/STATE.md), reconcile it with actual Git/task state, and maintain it at meaningful checkpoints and before pausing or ending. Tell the human what changed, what works with evidence, what remains uncertain, and what happens next.

Update an owned one-off prompt to remaining work, or retire it when completed/superseded after preserving decisions and evidence. Update its active references. Keep reusable templates and other sessions' work intact. A saved prompt or old handoff is not authority to replay completed work; verify its status first. Keep durable state outside this chat so another session can continue.
