> Public edition `public-development-v1-20260913`. Adapted from the reviewed architecture baseline; names in the source may still say Comreton. See [publication and authority](PUBLICATION.md). Development sequencing is governed by [DEVELOPMENT](../DEVELOPMENT.md); self-development is deferred until all four usable v0.1 releases.

# Research, critique, and the design contribution

Current follow-through: [CBR memory engine](https://github.com/Combraton/cbr/blob/main/docs/spec/MEMORY-ENGINE.md) and [bounded model-runtime design](https://github.com/Combraton/cbr/blob/main/docs/spec/MODEL-RUNTIME.md) incorporate the September 12 discussion. The Pi source snapshot supplies candidate API evidence only; no SDK release, packaging choice or model performance is established. [HANDOFF](HANDOFF.md) separates confirmed direction from unresolved implementation decisions.

> Evidence review dated 8 September 2026. “Verified” below means the named page or source location was inspected; it does not mean the proposed Comreton mechanism has been implemented or benchmarked.

## 1. Method and confidence

The initial corpus contained 31 `docs` files and 12 `claude-docs` files, including six long research notes. Five design-prompt files appeared in `claude-docs/design-prompts` during this pass and were also read, bringing the reviewed source set to 48 files (44 Markdown and four text files). The original product material defines the intent; Claude's synthesis and notes provide mechanisms and arguments to test. The Desktop architecture supplies additional reference only. Explicitly open sections are excluded as design inputs.

This pass directly checked five pinned GitHub source files and current primary documentation for critical runtime, history, incremental evaluation, evidence, harness, UI, and storage claims. Additional empirical papers were inspected at their abstract/publication pages; their numerical findings are not treated as independently reproduced results. The supplied research's other repository inspections remain inherited research, not new full-codebase verification.

The first delegated audit overstated its reading coverage and imported several recommendations that contradict the owner. Its raw conclusions were not adopted as authority. A bounded retry was used for complete coverage of the six long research notes; [the source audit (historical; not included)](PUBLICATION.md#historical-material) records actual coverage and the remaining limits.

## 2. Direct source checks

| Source inspected | Observed mechanism | Design use and limit |
|---|---|---|
| [Temporal completion validation](https://github.com/temporalio/temporal/blob/2220587dea828d938fc99253e178a13d1cb658c5/service/history/api/activity_util.go#L58) | Completion checks include attempt and version comparisons | Fence stale results; does not stop an already executed side effect |
| [jj operation/view structures](https://github.com/jj-vcs/jj/blob/2133040a8b99df306b3b6a199608b5ae669ae8a6/lib/src/op_store.rs#L249) and [operations](https://github.com/jj-vcs/jj/blob/2133040a8b99df306b3b6a199608b5ae669ae8a6/lib/src/op_store.rs#L346) | Views and operations are distinct, with parents and predecessor metadata; local history is distinguished from actual working-copy state | Adopt operation/view separation and explicit code anchors; do not turn jj's local operation log into our federation protocol |
| [Salsa backdating](https://github.com/salsa-rs/salsa/blob/65604afad5ff1036d2b883444d60c698bf531079/src/function/backdate.rs#L15) | Equality, durability, and provisional/cycle conditions constrain reuse; untracked reads are diagnosed | Use dependency-aware reuse only where comparator and dependency coverage justify it |
| [Dagster status resolver](https://github.com/dagster-io/dagster/blob/d201218e70782ea9ae4a0f3b6b20cd3cda3a3b13/python_modules/dagster/dagster/_core/definitions/data_version.py#L434) | Computes status from versions/causes; has domain-specific fresh shortcuts for some unsupported/external cases | Borrow provenance and cause trees; reject fresh-by-default for unobserved runtime truth |
| [in-toto Statement](https://github.com/in-toto/attestation/blob/2dcd055e9f72e746687c306e35f4e59720ff45be/spec/v1/statement.md) | Digest-identified immutable subjects and a typed predicate | Use compatible statement shape; domain verification and trust remain our responsibility |

Pinned source checks establish behavior at those commits, not current HEAD. Local SHA-256 digests and source URLs are preserved in [the source-check manifest (historical; not included)](PUBLICATION.md#historical-material).

## 3. Current primary documentation

| Source | What it supports | What we avoid inferring |
|---|---|---|
| [Temporal activity definition](https://docs.temporal.io/activity-definition) | Retryable activity work needs application/provider idempotency | Generic exactly-once side effects |
| [Bazel BEP](https://bazel.build/remote/bep) | Announced events and missing descendants expose incomplete output | A deadline proves death or no external effect |
| [jj operation log](https://docs.jj-vcs.dev/latest/operation-log/) | Inspect/undo/revert/restore through operation history | Reverting a plan undoes deployments or arbitrary runtime state |
| [Salsa algorithm](https://salsa-rs.github.io/salsa/reference/algorithm.html) | Tracked dependencies and equal-output backdating | Unchanged code text proves unchanged behavior |
| [ACP v1 prompt turn](https://agentclientprotocol.com/protocol/v1/prompt-turn) and [draft v2 session API](https://docs.rs/agent-client-protocol/latest/agent_client_protocol/struct.V2Session.html) | Different lifecycle mappings; draft v2 is explicitly unstable | Universal stable ACP-v2 support across harnesses |
| [Codex app-server](https://learn.chatgpt.com/docs/app-server) | Rich native thread/turn integration, version-specific schemas, experimental features | Every transport or method is production-stable or reattachment-safe |
| [Claude hooks](https://code.claude.com/docs/en/hooks#precompact) | Documented compaction boundary hooks and their limitations | Uniform hook support across harnesses or unlimited safe compaction blocking |
| [OpenTelemetry traces](https://opentelemetry.io/docs/concepts/signals/traces/) | Parent relationships and optional span links encode observed causality | A trace is complete or every async edge must use links |
| [SQLite atomic commit](https://www.sqlite.org/atomiccommit.html) | Local transaction durability mechanisms and assumptions | Atomicity with external processes, files, or other service databases |
| [Excalidraw API](https://docs.excalidraw.com/docs/@excalidraw/excalidraw/api), [React Flow performance](https://reactflow.dev/learn/advanced-use/performance) | Candidate renderer interfaces and performance considerations | Either satisfies the whole continuous-canvas product without a prototype |

## 4. Empirical and theoretical checks

[Build Systems à la Carte](https://www.microsoft.com/en-us/research/publication/build-systems-a-la-carte/) separates scheduling dependencies from deciding whether recomputation is needed. We use that distinction inside CBR; human methodology and harness behavior remain separate from an incremental build engine.

[LongMemEval](https://arxiv.org/abs/2410.10813) evaluates extraction, cross-session reasoning, time, updates, and abstention. These inspire CBR fixtures, but chat-memory accuracy does not establish software-project truth or runtime correctness.

[Evaluating AGENTS.md, version 2](https://arxiv.org/abs/2602.11988v2) reports that repository context files did not generally improve success in its tested settings and increased average inference cost. This is evidence against assuming that more context is inherently useful. It does not prove task-specific, cited, current packets cannot help.

The [METR early-2025 developer productivity study](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/) motivates measuring actual developer time against perceived benefit. Its participants, tools, and period differ from our proposed product. We use the evaluation discipline, not its effect size as a Comreton prediction.

## 5. Disposition of Claude's major proposals

| Proposal | Disposition | Reason |
|---|---|---|
| “Build system for project truth” as the product definition | Restrict to CBR mechanism | Loses the owner's human-operated spatial orchestration product |
| Single writer, intent before effect, separate product journals | Adopt with explicit local atomic transactions | Clear ownership and recoverable obligations; no cross-store atomicity implied |
| Extending the build-system analogy to every relationship (a risk in interpreting the proposal) | Explicitly prevent | Workflow, evidence lineage, operation history, and runtime causality differ |
| Incremental provenance and early cutoff | Adopt with scope/coverage limits | Useful for tracked deterministic derivations; not semantic truth by hashing |
| Never store status anywhere | Reject the absolute rule | Version-stamped materialized projections are legitimate; canonical facts own meaning |
| Contradictions as conflicted values | Combine with durable conflict records | Prevent accidental reads while preserving reasons and resolution history; separate desired/observed drift |
| Machine edits auto-merge while human edits require current head | Reject for semantic edits | Author type does not establish safe merge; use semantic conflict checks for both |
| ACP v2 as universal floor | Reject | Negotiate actual version and capability; keep native adapters and limited PTY mode |
| Expected events and announced children | Adopt selectively | Detect lifecycle/artifact incompleteness; persist timers; keep unknown effects after waits close |
| Every result signed and every attempt SLSA provenance | Narrow | Use appropriate typed attestations; signatures establish attribution, not truth |
| Force-destroy on failed reattach | Reject | Failure to reattach does not prove process ownership or authorize termination |
| EEVDF, Plan 9 namespace, React lanes as mandatory kernel design | Reject mandatory adoption | Borrow fairness, scoped access, and grouped attention with simpler domain mechanisms |
| Attention queue as home | Reject | Direct conflict with the original infinite-canvas home and attention lens |
| `truth.lock` and sidecar storage | Adopt optional export | Useful portable evidence view; cannot validate unavailable runtime observations offline |
| Tiered packets, omissions, stable rendering | Adopt with measurement | Context budget, retention after compaction, and required constraints need explicit handling |
| Run cache for identical prompts | Restrict to artifact reuse | Model output and external effects are not generally reproducible |
| N repeated observations auto-accept interpretations | Reject as a generic rule | Correlated sources or repeated models are not independent proof |
| Trace-based runtime verification and negative controls | Adopt for selected contracts | Distinguish intended/old path; do not impose a journey on every task |
| Retention by tracing roots and leases | Adopt with all retained branches as roots | Older experiments must remain inspectable/restartable, not just the current accepted view |
| In-house signed-envelope implementation and fixed dependency/license choices | Reassess before adoption | Prefer vetted encoding/signing/verification components and current compatibility/license assessment; the source already proposes a signature library, not a new cryptographic primitive |

The later design prompts reinforce useful glyphs, invariant-preserving zoom, and evidence correction actions. Their claims that a session is a workflow, attention is home, the UI owns no presentation state, and invalid regions may silently become informational are rejected. Their colors, typography, counts, and sample project data are design proposals, not architecture requirements.

The Desktop architecture's existing-PIO/MBR preservation mandate is superseded by the owner's fresh-build instruction. Its useful transaction, ownership, and corrected template distinctions survive after independent review.

## Human oversight and autonomy review, 12 September

The owner confirmed the behavior in [STEERING](STEERING.md): routine scoped investigation/repair continues, the human stays oriented, and intervention concerns needed direction/authority changes or reserved judgments. This is a product decision informed by research, not an experimentally validated Comreton result.

- [AI Agents Push Humans Out of the Loop, v3](https://arxiv.org/html/2608.23642v3) is a position paper. It recommends cognitive support, bounded autonomy and selective decision design; it does not validate a particular coding control plane. We take attention cost seriously without treating its proposed behavioral monitoring as an approved product feature.
- [Human-in-the-Loop User Feedback Affects Perceived Accuracy and Trust, v1](https://arxiv.org/html/2607.17548v1) reports classification experiments in which interaction and task context affected perception. Mandatory feedback, simulated model updates and differences between task domains limit causal transfer to long-running coding. Approval and confidence must not substitute for correctness evaluation.
- The requested [Dex Horthy X post](https://x.com/dexhorthy/status/2081797628552270027) could not be retrieved directly in the review. [HumanLayer’s own index](https://www.humanlayer.com/blog/humanlayer-resources) links the related [benchmark report](https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/benchmarking-opus-5-on-slop-code-bench.md) and [software-factory essay](https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/wsff.md). The essay supports earlier alignment and reviewable slices while explicitly scaling process by task size. We do not treat every task as needing its full methodology or infer a guarantee from benchmark anecdotes.

Our composed steering view, scoped waiting and transition-specific gates are accepted architecture choices; their product benefit remains an engineering hypothesis. [PLAN](PLAN.md) requires comparison with native harness use and a permission-heavy variant, including human reorientation and intervention costs.

## 6. Candidate contribution of this architecture

The contribution is the composition, not an invention claim about individual mechanisms:

1. **A shared, versioned basis for acting and accepting.** A harness starts with a declared plan/context/code basis; its result is adopted only against relevant current dependencies. This connects context selection to execution and proof.
2. **Branchable project history beyond code.** A checkpoint preserves methodology instance, graph, decisions, evidence, and code references, with an honest restart plan for external effects and native context gaps.
3. **A spatial surface with semantic parity.** Drawing, CLI, and harness access operate on the same revisions and authority rules; time and evidence stay attached to the work the human recognizes.
4. **Independent products that compose tightly.** PIO and CBR retain narrow owners and useful standalone profiles, while Comreton supplies the missing project-level coordination.

Each can fail: read-set coverage can be incomplete, history can become expensive, the canvas can become confusing, and coordination can add more overhead than it saves. The [plan](PLAN.md) tests these failure modes. Novelty and benefit remain hypotheses until supported by comparison and user evidence.

## Final disposition: preparation and programmatic context, 12 September

The [background learning and timely-context assessment (historical; not included)](PUBLICATION.md#historical-material) remains a dated research report. Its ownership-compatible recommendations are now incorporated in [CBR preparation/delivery](https://github.com/Combraton/cbr/blob/main/docs/spec/PREPARATION-AND-DELIVERY.md) and [model runtime](https://github.com/Combraton/cbr/blob/main/docs/spec/MODEL-RUNTIME.md): bounded consolidation, fast binding corrections, progressive assimilation, explicit timing obligations, fresh continuations and optional constrained programmatic workers.

Full Prime/Pi adoption, automatic policy self-refinement and universal numerical thresholds were not selected. The pinned source observations establish candidate mechanics and limitations, not CBR outcome quality. [BASELINE](BASELINE.md) and [DECISIONS](DECISIONS.md) supersede the report's earlier request for another architecture discussion. Cold initialization, refresh, total cost and downstream outcomes remain in the evaluation plan.
