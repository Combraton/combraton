> Public edition `public-development-v1-20260913`. Adapted from the reviewed architecture baseline; names in the source may still say Comreton. See [publication and authority](PUBLICATION.md). Development sequencing is governed by [DEVELOPMENT](../DEVELOPMENT.md); self-development is deferred until all four usable v0.1 releases.

# Architecture decisions and implementation selections

> Accepted baseline `architecture-v1-20260912`, finalized at the owner's request on 12 September 2026. The behaviors below are settled for the build. Component choices and measured defaults remain bounded implementation tasks in [BASELINE](BASELINE.md).

## Accepted decisions

| Decision | Selected behavior | Reason and alternative |
|---|---|---|
| D1: Authority | Comreton controls project direction/readiness/acceptance; PIO owns execution facts; CBR owns evidence/context | Coordination costs more than a monolith but preserves independent use and avoids competing controllers. |
| D2: History | Immutable revisions, retained branches, successor runs and explicit reuse | More metadata than editing a live run; preserves causality and experiments. External effects still need reconciliation. |
| D3: Persistence/communication | Independent transactional authorities, outbox/inbox, idempotent commands and versioned profiles | Shared writable tables would couple releases and authority. Rust/SQLite/local JSON-RPC remain reference implementation preferences at defined selection milestones. |
| D4: Applicability | Evidence/provenance and reuse under documented dependency coverage | Extra rechecking avoids false certainty. Similar embeddings or recent prose alone do not validate a claim. |
| D5: Steering | Scoped autonomous investigation/repair; separate visibility, decisions and enforcement; transition-specific gates | Avoid routine approval fatigue while retaining real authority boundaries. See [STEERING](STEERING.md). |
| D6: Spatial product | Zoom is navigation; every containment level is a canvas; renderer serves the same semantic model as alternate views | More demanding than a flat node editor. Select the library through an early interaction prototype. |
| D7: Build/evaluation | Standalone PIO/CBR proof, integrated loop, history/templates/canvas, sustained comparison | Slower than a visual demo; avoids treating an impressive interface as execution or memory proof. |
| D8: CBR lifecycle | Two bounded memory procedures, typed commits, recorded derivations, rebuildable indexes, memory views and exact packets | More provenance than notes. Original evidence remains available when summaries lose relationships. Model assistance is central, not project authority. |
| D9: PIO mechanics | Invocation journal before dispatch, fenced claims, unresolved usage liability and immutable completion | More explicit unknown states; reduces silent duplication and false success. Borrow Puppetmaster mechanics without its controller policy. |
| D10: Preparation | Background consolidation, fast binding corrections, progressive brownfield assimilation and early greenfield capture | Amortizes useful investigation without a global startup barrier. Broader preparation is optional and its costs count. |
| D11: Timely context | Caller-selected advisory/start/transition requirements; exact basis/delivery; no scarce consumer reservation while waiting for its preparation | Adds coordination but avoids late-context prevention claims and deadlocks. See [CBR delivery](https://github.com/Combraton/cbr/blob/main/docs/spec/PREPARATION-AND-DELIVERY.md). |
| D12: Worker boundary | Direct calls and a small memory-specific loop; optional constrained programmatic workers | Batching can reduce context without mandatory recursion. Full Prime/Pi adoption is unselected; CBR retains policy, budgets, provenance and commit authority. |
| D13: Methodology | Optional templates, stage groups and blueprints; actual harness graphs execute; standard/custom use the same operations | Supports small bugs and long methodologies. Excludes global mandatory stages, executable template scripts and fake stage nodes. |

## Consequences that must not drift

An execution result is not project acceptance. A cited inference is not a runtime observation. Delivery acknowledgment is not comprehension. Agreement based on the same artifact is not independent corroboration. Branch selection is not external rollback. A displayed restriction is not OS enforcement.

CBR may publish authorized memory revisions through validation; it cannot change selected project direction or its own trust/permission policy. Procedure/prompt changes are separately versioned and evaluated proposals. Comreton may hold a required transition without stopping independent authorized work. Default grants and provider limitations remain inspectable.

## Choices delegated to implementation evidence

The [selection table](BASELINE.md) assigns schema freeze, SDK/language packaging, sandbox backend, renderer, model qualification, numerical limits and review defaults to milestones. Research citations, example token counts and inherited package names do not select dependencies. These need recorded evidence, not another blanket architecture approval ceremony.

If a candidate cannot satisfy the accepted semantics, document the failed fixture and propose a bounded architecture change. Otherwise implement within the baseline and record the selected component/version. A future build instruction specifies the phase; this task finalizes documentation only.

## Subsequent accepted decision: standalone-first development

[ADR 001](../decisions/001-standalone-first-and-evaluation.md), accepted 13 September 2026, replaces the earlier early-Combraton integration sequence. Protocol, PIO and CBR reach agreed independent release gates and combined standalone validation through PIO's CLI/TUI before Combraton implementation. Separate benchmark infrastructure measures public behavior; core ownership remains unchanged.
