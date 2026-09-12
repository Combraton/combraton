> Public edition `public-development-v1-20260913`. Adapted from the reviewed architecture baseline; names in the source may still say Comreton. See [publication and authority](PUBLICATION.md). Development sequencing is governed by [DEVELOPMENT](../DEVELOPMENT.md); self-development is deferred until all four usable v0.1 releases.

# Architecture handoff: start here

> Finalized architecture baseline `architecture-v1-20260912` · 12 September 2026. The owner explicitly requested consolidation and finalization after review. Architecture agreement is complete for this baseline. Wire schemas, components and performance still require implementation evidence. This documentation task has not implemented the product.

## 1. Product objective and fixed boundaries

Comreton is the human-steered spatial control plane for large greenfield and brownfield projects built with existing harnesses. Success is better accepted work and less reconstruction/steering effort than disciplined native harness use, accounting for time, cost and attention.

- Comreton owns selected direction, workflow readiness, project reliance/acceptance and branch adoption.
- PIO owns execution, workspace/process/session identities, receipts, usage and recovery. Preserve native investigation/edit/test loops.
- CBR owns evidence, model-assisted memory revision, applicability and exact context. Small discoveries and long projects use bounded jobs with durable progress outside model context.
- Routine investigation and repair continue within agreed scope. Keep work understandable; request intervention for a needed change of direction, authority or reserved judgment. Block specific governed transitions, not all work.
- PIO, CBR and the protocol are independent products. Compose public profiles without shared writable databases.
- Templates are optional methodology/configuration; workflows are actual harness graphs. Standard/custom templates share operations. Stages add neither harness nodes nor canvas levels.
- Semantic zoom navigates orchestra, project, session and workflow canvases, with native harness detail and equivalent alternate views.
- History retains revisions and alternative branches. Restart creates a successor with explicit reuse; it does not undo external effects.

## 2. Decision status—do not infer missing selections

| Status | Meaning |
|---|---|
| Accepted architecture | [BASELINE](BASELINE.md) and D1–D13 in [DECISIONS](DECISIONS.md); implement these semantics without reopening the whole design |
| Detailed contracts | Current shared/domain specs elaborate the baseline; conceptual sketches require schema work |
| Implementation selections | Models, SDKs, schemas, enforcement, renderer and numerical defaults have explicit milestones in BASELINE |
| Unproven hypotheses | Better outcomes, less context waste, useful anticipation and reduced reconstruction require PLAN's comparisons |
| Historical evidence | Research, originals, old assessments and snapshots explain rationale and do not override current decisions |

“Finalized” does not mean an installed SDK, approved model, tested security boundary or frozen wire API. An unselected library is not a reason to postpone schema/evidence-kernel work or repeat the entire architecture review.

## 3. Read current sources in this order

1. [BASELINE](BASELINE.md), [DECISIONS](DECISIONS.md), [VISION](VISION.md), [ARCHITECTURE](ARCHITECTURE.md), [STEERING](STEERING.md).
2. [MODEL](MODEL.md), [TEMPLATES](TEMPLATES.md), [HISTORY](HISTORY.md), [FLOWS](FLOWS.md), [UI](UI.md).
3. [PIO spec](https://github.com/Combraton/pio/blob/main/docs/spec/SPEC.md) and [internals](https://github.com/Combraton/pio/blob/main/docs/spec/INTERNALS.md).
4. [CBR spec](https://github.com/Combraton/cbr/blob/main/docs/spec/SPEC.md), [memory engine](https://github.com/Combraton/cbr/blob/main/docs/spec/MEMORY-ENGINE.md), [preparation/delivery](https://github.com/Combraton/cbr/blob/main/docs/spec/PREPARATION-AND-DELIVERY.md), [bounded runtime](https://github.com/Combraton/cbr/blob/main/docs/spec/MODEL-RUNTIME.md), [internals](https://github.com/Combraton/cbr/blob/main/docs/spec/INTERNALS.md).
5. [Protocol](https://github.com/Combraton/protocol/blob/main/docs/spec/SPEC.md), [VERIFICATION](VERIFICATION.md), [STORAGE](STORAGE.md), [EXTENSIONS](EXTENSIONS.md), [PLAN](PLAN.md).
6. [RESEARCH](RESEARCH.md) for source limitations or a specific component investigation.

The current public Markdown is authoritative. [Publication provenance](PUBLICATION.md) and [the import manifest](source-import.json) identify the imported source and owning repositories. The local HTML reading edition is not published here.

## 4. Source authority and conflicting documents

The owner's latest instructions control. BASELINE and DECISIONS record the selected architecture; current domain and shared specs elaborate it together. Resolve concrete inconsistencies against the baseline, not filename, modification time, research examples or old code.

`reference/original-20260908`, `reference/revisions`, `cbr/revisions`, dated reviews/research reports, the memory research guide and external `claude-docs` are historical or explanatory. Their older review status describes their own date. Marked-open sections in original sources were excluded as inherited inputs; this does not erase explicit implementation selections in the current baseline.

Pre-baseline snapshots remain in the original design archive and are not included here. Existing implementations and the Desktop architecture are fresh-build references, not adopted dependencies.

## 5. Distinctions that prevent implementation drift

Keep separate: authority and execution facts; memory publication and project acceptance; artifact revisions, memory views and exact packets; normative direction and observed behavior; declared coverage and complete world knowledge; recorded decisions, delivered steering and subsequent behavior.

CBR background preparation is part of its maintenance loop. Binding corrections remain accessible before consolidation. Brownfield assimilation is progressive, without a global “repository understood” barrier. The caller selects bounded context obligations and their timing; PIO does not invent knowledge policy. CBR's optional harness investigation has its own identity/grant; waiting consumers cannot monopolize its needed resources.

Direct calls, tool loops and optional programmatic workers obey aggregate budgets, scope and provenance. A Python heap or SDK conversation is not canonical memory. Million-token windows and full Prime/Pi forks are not prerequisites. Enforcement and observation limits must be reported truthfully.

## 6. Where implementation starts

Phase 0 is complete as an architecture baseline. Begin a later authorized build with [PLAN Phase 1](PLAN.md): schemas/failure fixtures and spatial interaction prototyping. Resolve components at their milestones. Prove PIO and CBR independently, then one integrated migration/repair/steering/restart story before broad expansion.

Unknown required semantics fail explicitly until their contract is defined. Documentation examples are not generated API specifications. Do not claim a phase complete from diagrams or fake providers where PLAN requires real adapters or downstream outcomes.

## 7. Suggested prompt for a new build session

```text
Use docs/architecture/HANDOFF.md in Combraton/combraton as the entrypoint.
Implement the phase I specify from finalized architecture-v1-20260912.
Read BASELINE.md, DECISIONS.md, PLAN.md and relevant shared/domain contracts.
Preserve ownership, independent use, scoped autonomous repair, semantic zoom,
optional templates, retained history and truthful evidence.
Freeze concrete schemas/conformance fixtures before relying on wire semantics.
Resolve ordinary components through the documented selection milestones;
do not assume a model, Pi/Prime SDK, sandbox or example number was selected.
Historical research and old implementations cannot override current specs.
If a choice changes accepted architecture, identify the precise change and reason.
Report what is implemented, tested and still unproven.
```
