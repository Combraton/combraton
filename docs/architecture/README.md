> Public edition `public-development-v1-20260913`. Adapted from the reviewed architecture baseline; names in the source may still say Comreton. See [publication and authority](PUBLICATION.md). Development sequencing is governed by [DEVELOPMENT](../DEVELOPMENT.md); self-development is deferred until all four usable v0.1 releases.

# Comreton: finalized architecture and build handoff

> Finalized baseline `architecture-v1-20260912` · 12 September 2026 · Documentation only. [BASELINE](BASELINE.md) records accepted architecture and bounded implementation selections. [HANDOFF](HANDOFF.md) is the entrypoint for a build session.

**Comreton is an orchestrator for agentic work: a spatial control plane where workflows are drawn, nodes are existing agentic harnesses, and the project's truth stays synchronized with the human, the agents, and the running code.**

The target is large greenfield and brownfield software work that lasts across many sessions. Success means better accepted results than using Codex, Claude Code, or another harness individually, at an acceptable cost in time, money, and human attention. More agents, more documents, and more checks are not success by themselves.

## Read this in three passes

Use the Markdown map below for the complete public baseline. The original local HTML reading edition is historical and is not published here. GitHub renders the Mermaid diagrams in the current chapters.

**Start a new session with [HANDOFF](HANDOFF.md).** The current CBR design includes an [active memory engine](https://github.com/Combraton/cbr/blob/main/docs/spec/MEMORY-ENGINE.md) and [bounded model runtime](https://github.com/Combraton/cbr/blob/main/docs/spec/MODEL-RUNTIME.md). [PIO internals](https://github.com/Combraton/pio/blob/main/docs/spec/INTERNALS.md) specify execution mechanics. The [September 9 assessment (historical; not included)](PUBLICATION.md#historical-material) is historical rationale, not a competing current specification.

Start with [the product](VISION.md), [the architecture](ARCHITECTURE.md), and [accepted decisions and implementation selections](DECISIONS.md). These explain the architecture without requiring you to know the internal record names.

Read [human steering with room to experiment](STEERING.md) for the confirmed principle, concrete migration example, shared steering view and remaining choices.

Then follow one [worked example](FLOWS.md), read [templates and workflows](TEMPLATES.md), and explore [history and restart](HISTORY.md) and [the spatial interface](UI.md). This is the product you would actually operate.

Finally, review the independent designs for [PIO](https://github.com/Combraton/pio/blob/main/docs/spec/SPEC.md), [CBR](https://github.com/Combraton/cbr/blob/main/docs/spec/SPEC.md), and [the protocol](https://github.com/Combraton/protocol/blob/main/docs/spec/SPEC.md), alongside [verification](VERIFICATION.md), [storage and recovery](STORAGE.md), and [future integrations](EXTENSIONS.md). [The plan](PLAN.md) turns these contracts into a dependency-ordered build and evaluation program from the accepted baseline.

| Document | Question it answers |
|---|---|
| [VISION](VISION.md) | What are we building, and which original ideas must survive? |
| [ARCHITECTURE](ARCHITECTURE.md) | Who owns each responsibility, and how does the whole system work? |
| [STEERING](STEERING.md) | How do harnesses iterate freely while the human stays informed and consequential transitions remain controlled? |
| [MODEL](MODEL.md) | What exactly are projects, sessions, templates, revisions, runs, and claims? |
| [TEMPLATES](TEMPLATES.md) | How does reusable methodology become actual harness graphs? |
| [HISTORY](HISTORY.md) | How do inspection, branching, correction, reuse, and pruning work? |
| [FLOWS](FLOWS.md) | What happens step by step in real project scenarios? |
| [UI](UI.md) | How does the human draw, understand, steer, and revisit the work? |
| [PIO](https://github.com/Combraton/pio/blob/main/docs/spec/SPEC.md) | How are harnesses controlled and recovered without inventing capabilities? |
| [CBR](https://github.com/Combraton/cbr/blob/main/docs/spec/SPEC.md) | How are evidence, project knowledge, and context kept useful over time? |
| [CBR MEMORY ENGINE](https://github.com/Combraton/cbr/blob/main/docs/spec/MEMORY-ENGINE.md) | How does CBR actively investigate, maintain artifacts and serve requests? |
| [CBR MODEL RUNTIME](https://github.com/Combraton/cbr/blob/main/docs/spec/MODEL-RUNTIME.md) | How are CBR's own context limits handled, and which SDK choices remain open? |
| [BASELINE](BASELINE.md) | What architecture is finalized, and where are implementation choices resolved? |
| [HANDOFF](HANDOFF.md) | What is finalized, what requires implementation selection, and what is historical? |
| [PROTOCOL](https://github.com/Combraton/protocol/blob/main/docs/spec/SPEC.md) | What crosses product boundaries, with which guarantees? |
| [VERIFICATION](VERIFICATION.md) | What is sufficient proof for a particular outcome? |
| [STORAGE](STORAGE.md) | What is durable, how is it recovered, and what may be deleted? |
| [EXTENSIONS](EXTENSIONS.md) | How can independent applications and remote systems participate? |
| [PLAN](PLAN.md) | In what order should we build, and how will we know it works? |
| [RESEARCH](RESEARCH.md) | What did we verify, borrow, modify, and reject? |
| [DECISIONS](DECISIONS.md) | Which architecture decisions are accepted, and what still requires implementation evidence? |
| [Source audit (historical; not included)](PUBLICATION.md#historical-material) | Was every supplied document accounted for? |
| [Validation (historical; not included)](PUBLICATION.md#historical-material) | Which documentation checks actually passed? |

## Authority and preservation

1. The owner's current instructions establish task authority; record lasting changes before dependent work relies on them.
2. BASELINE and DECISIONS record the accepted architecture. Current shared/domain chapters elaborate it. Component selections and performance remain subject to implementation evidence.
3. Each current chapter has one owning public repository. [Publication provenance](PUBLICATION.md) describes the original source, import transformations and excluded historical material.
4. Research, old implementations, previous validation and source snapshots cannot override the current baseline. Their archived files are not included in this public edition.
5. [DEVELOPMENT](../DEVELOPMENT.md) governs the development process and supersedes older bootstrap sequencing. Self-development is deferred until all four usable v0.1 releases.

If current sources contradict one another, identify and resolve the specific conflict rather than silently inventing a resolution. The historical material's marked-open proposals are not an inherited task list. Explicit unselected implementation components in the accepted baseline still need bounded selection work.

Code blocks describe conceptual contracts and examples; they are not implemented APIs. Diagrams depict the target system. Exact package versions, production performance, harness conformance, and product benefits have not been established by this documentation pass.

Read [CBR preparation and delivery](https://github.com/Combraton/cbr/blob/main/docs/spec/PREPARATION-AND-DELIVERY.md) for background consolidation, progressive assimilation and context timing. The [finalization report (historical; not included)](PUBLICATION.md#historical-material) records scope and validation.

## Current standalone-first build order

[ADR 001](../decisions/001-standalone-first-and-evaluation.md) supersedes the earlier early-Combraton implementation sequence. Start with Protocol; complete PIO and CBR standalone scopes in parallel; validate them together through PIO's CLI/TUI and benchmark clients; then begin thin Combraton. [Release gates](../STANDALONE-RELEASES.md) define readiness.
