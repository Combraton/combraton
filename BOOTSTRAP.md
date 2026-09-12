# Bootstrap and development operating model

> Initial repository setup, 13 September 2026. This plan applies the reviewed architecture; it does not declare implementation milestones complete.

## Source of truth before the product can coordinate itself

Use versioned architecture/decisions for design, repository issues for bounded work, pull requests for changes, CI artifacts for checks, and one concise milestone summary for current integration state. Chat is a working surface, not the only durable record. A coordinating agent session must be replaceable.

The first follow-up is to import and reconcile the applicable finalized architecture documents from the existing design workspace. Establish a canonical cross-system baseline here, domain specifications in their owning repositories, and versioned contracts in protocol. Preserve historical research separately. Do not independently edit four copies of the full corpus.

The repository setup does not yet include that import, a GitHub Project, issues, branch rules, implementation CI or local clones. Add them as bounded follow-up work after source ownership and local checkout locations are established.

## Milestones

| Milestone | Result and evidence |
|---|---|
| Repository bootstrap | Four independent repositories with scope/status READMEs and agent entrypoints |
| Reproducible development foundation | Canonical specs, build commands, first milestone issues and a fresh-session handoff that reproduces checks |
| Protocol foundation | Small execution/evidence/context contracts and negative fixtures for duplicates, missing data, stale basis and unsupported capabilities |
| PIO foundation | One real harness, durable invocation identity/output, cancellation and reconciliation; surviving-process and lost-ack tests |
| CBR foundation | Evidence sealing, typed revisions, bounded model-assisted investigation, exact packets and explicit applicability/gaps; continuation and source-change tests |
| Thin integrated control plane | Real task/context/execution/evidence/steering flow; failure, restart and correction demonstrated across all owners |
| Controlled self-use | Known working release coordinates selected changes to candidate code, with independent recovery and acceptance checks |
| Sustained self-development | Expand autonomy only after repeated use demonstrates reliable outcomes, continuity and manageable human effort |

PIO and CBR foundation work can proceed concurrently once their shared contract slice is stable. Develop only the protocol surface needed for the next integrated capability; avoid speculative full-schema expansion. UI assessment/prototyping proceeds alongside backend work. Full canvas/history/template releases retain the acceptance requirements in the canonical plan.

## Stack selection

| Area | Starting preference | What selects it |
|---|---|---|
| Durable service cores | Rust/Tokio | Packaging, lifecycle, recovery and maintainability experiment |
| Local storage | Independent SQLite stores plus content-addressed payload files | Transaction, restore, retention and fault fixtures |
| Wire transport | Versioned semantic profiles, bounded local JSON-RPC over authenticated sockets/pipes | Framing, identity, compatibility and failure tests |
| Desktop | React/TypeScript and native-shell candidate; assess existing Loom assets/code | Semantic zoom, service bindings, accessibility and performance evidence |
| CBR models/runtime | Provider abstraction, direct calls and small CBR-owned investigative loop | Context control, cancellation, total usage, provenance and restart comparisons |
| Optional programmatic workers | Deterministic batching first; constrained generated code only when justified | Sandbox/resource/capture tests and measured downstream benefit |

Architecture is finalized; these component choices and numerical defaults are not. Each experiment ends in a decision record naming the candidate/version, tests, limitations and fallback. Reopen architecture only when evidence exposes a specific incompatible invariant.

## Bounded issue and session contract

Each issue identifies the concrete problem, expected behavior, owning repository, dependencies, scope and acceptance evidence. Keep the upcoming milestone detailed and later milestones coarse. A cross-repository capability has an integration issue and linked component work.

On session start, inspect the issue, applicable architecture, actual checkout and current check results. On handoff, preserve commits/PRs, actual commands/results, unresolved facts and next action. Update relevant docs in the same change when behavior/contracts change. Do not claim completion from an agent summary alone.

Pin a tested integration combination of protocol/PIO/CBR/control-plane revisions. Individually passing repository checks do not prove compatibility. Contract changes must update fixtures and affected consumers; coordinate rollout without requiring unrelated repositories to change atomically.

## Self-development boundary

A known working release coordinates harnesses building the next candidate in separate workspaces. Candidate code does not overwrite the running controller or active stores. Test migrations on copies; retain native harness access and an external recovery procedure.

A run cannot redefine its own acceptance conditions to pass. Changes to verification policy are visible and separately assessed. Version adoption follows the selected authority and required checks. Start with small isolated development tasks before granting responsibility for changes to recovery, permissions or durable state.
