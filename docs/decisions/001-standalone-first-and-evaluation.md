# ADR 001: standalone-first releases and evaluation through PIO's client

- **Status:** accepted development direction and architecture clarification.
- **Date:** 13 September 2026.
- **Authority:** owner's explicit request to build Protocol, PIO and CBR as standalone projects, use PIO's TUI with CBR to test the three, and update the repositories.
- **Supersedes:** early thin-Combraton implementation in `development-v1-20260913`, the prior README build order, PLAN's earlier placement of standalone releases, and the corresponding recommendation in the dated ECC/development assessment.
- **Preserves:** control-plane/execution/evidence ownership, native scoped autonomy, independent stores, protocol profiles, exact context, retained history and deferred Combraton self-development.

## Decision

Define and implement the agreed standalone Protocol release surface first. PIO and CBR then develop in parallel against the recorded contracts to their agreed complete standalone release scopes. They may reveal necessary compatible protocol revisions; “first” does not mean an immutable protocol designed for every future system.

Validate the services together without Combraton through PIO's standalone CLI/TUI application and optional CBR integration. Complete standalone acceptance and release evidence before starting thin Combraton implementation. After that, use early Combraton experiments to challenge the interfaces and feed justified changes back through versioned contracts.

“Complete” means the agreed independent release scope is installable, documented and acceptance-tested. It is not restricted to a toy Combraton demo and does not require every possible future adapter, model or remote extension. Define supported capabilities and deferred extensions explicitly before implementation; do not silently reduce promised scope.

## Client authority clarification

PIO's terminal UI is a first-class presentation layer over its public execution API. A co-packaged standalone client application carries the user's explicit task/grant/context policy into public PIO and CBR calls. The client owns only its recoverable request/correlation state. PIO's execution core does not invent knowledge policy, and CBR does not grant project authority. Standalone human/caller authority replaces Combraton's role for these bounded operations; no hidden Combraton instance or mandatory project graph is required.

Combraton later calls the same service APIs directly. Its project/workflow/acceptance/history responsibilities are more than a different skin over PIO; it does not embed the TUI. [Standalone client contract](https://github.com/Combraton/pio/blob/main/docs/spec/STANDALONE-CLIENT.md) specifies discovery, multi-harness use, optional context, failure and reciprocal-call boundaries.

## Evaluation ownership

Create `Combraton/benchmarks` as public evaluation infrastructure, not a fifth runtime service. Protocol owns normative conformance fixtures; services own component/adapter tests; benchmarks owns composition scenarios, experimental methodology and result manifests. It calls public interfaces and pins tested revisions. An integration pass is scoped evidence of interoperability, not proof of every protocol profile or superior agent outcomes.

## Alternatives and trade-offs

Early Combraton integration would expose desktop needs sooner but would not meet the owner's requested standalone-first sequence. Fully isolated development with no combined PIO/CBR use would preserve independence but postpone compatibility feedback. The selected middle ground is standalone product completion with combined public-interface validation before the desktop.

A benchmark suite inside Protocol would blur normative contracts and comparative experiments. A benchmarks runtime embedded in the products would create circular dependencies and risk measuring privileged paths. A separate repository keeps experiments replaceable, though maintainers must pin versions and coordinate fixture updates explicitly.

## Evidence and implementation status

This is a selected plan, not a measured product result. [Release criteria](../STANDALONE-RELEASES.md) define the readiness gates. [Evaluation methodology](https://github.com/Combraton/benchmarks/blob/main/docs/METHODOLOGY.md) defines strong native baselines, repeated trials, failure accounting and source references. Renderer, SDK/model, numeric budget and benchmark-runner selection still need bounded experiments. Current repositories contain documentation/setup; no standalone runtime or benchmark pass is implied.
