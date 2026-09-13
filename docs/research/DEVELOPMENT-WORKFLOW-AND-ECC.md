# Research: developing four independent products with Claude Code and Codex

> Historical assessment. [ADR 001](../decisions/001-standalone-first-and-evaluation.md) subsequently superseded this report's early-Combraton integration recommendation. ECC source findings remain the dated assessment; use current DEVELOPMENT and standalone release gates for build order.

Reviewed 13 September 2026. Recommendation: **use a small repository-centered workflow; adapt selected ECC ideas; do not install ECC as the shared development platform now.** This is a source-backed engineering assessment, not a benchmark proving that the proposed workflow improves results.

The resulting operating agreement is [DEVELOPMENT](../DEVELOPMENT.md). Architecture remains governed by the [public edition](../architecture/PUBLICATION.md). Combraton self-development is deferred until usable v0.1 releases of all four projects.

## Questions and method

We need four independent products to converge on real journeys while using current coding agents. The risks are conflicting contracts, lost decisions, duplicated work, excessive context, misleading verification and a human reduced to approving unexplained changes. The objective is high-quality parallelism, not maximum agent count.

The review covered the supplied official guidance and both supplied community discussions. ECC was shallow-cloned and source-inspected at commit `8321021c54d670126ce3b2969d5deb880b4b0c2a`, whose package identifies itself as `ecc-universal` version `2.2.1`. The relevant installer, reference configuration, hook, memory, worktree and verification paths were inspected. A bounded secondary source audit was checked against the actual files; unsupported findings were discarded. No ECC installation, hooks, test suite or global configuration changes were executed. Existence of a test file is evidence of a test definition, not evidence that it passes in our environment.[^ecc-package]

Loom was inspected through its browser accessibility surface and selected source paths. Its shared world declares simulated data. This review did not perform a full interactive, accessibility or performance certification of the mock.

## What the supplied research supports

OpenAI's harness-engineering article describes a team making repository knowledge discoverable through short instructions, versioned design/plan documents and mechanical checks. Its experience supports an entrypoint that points to deeper knowledge. It also describes agents inspecting an isolated running application and observability data. We adopt that emphasis on legibility and observable behavior. The article's speed estimates and agent-heavy merge practices come from one internal experience; they do not establish our expected speedup or justify removing human judgments.[^openai-harness]

Anthropic's large-codebase guidance explains that instruction scope, working directory and access to adjacent repositories matter. Instructions and configuration do not have identical inheritance rules. Accessing another directory does not guarantee its instructions were loaded. Our consequence is explicit repository entrypoints and small task-specific reading sets. Splitting into four repositories helps ownership but does not automatically create coherent context.[^claude-large]

The first Reddit discussion recommends a documentation map, bounded plans and ADRs so a fresh session can recover prior decisions. We adopt those principles while avoiding the full sprint ceremony in its example. The second discussion includes research before planning, smaller implementation chunks and fresh sessions; it also illustrates the inconvenience of manually relaying information between chats. These are practical experience reports, not controlled comparisons. They do not settle permanent Claude-versus-Codex roles.[^reddit-one][^reddit-two]

## Instructions that cooperate instead of duplicating

Claude Code officially supports importing `AGENTS.md` from `CLAUDE.md` using `@AGENTS.md`. Imports enter the context window; importing every architecture chapter would defeat the purpose of a short map. We use the local shared instruction file plus a few Claude-specific notes.[^claude-memory]

Codex discovers instruction files along the path from the project root to the current directory, with more local instructions applied later. Its documented combined project instruction limit is a ceiling, not a size target. Root-launch discovery should not be confused with recursively loading every nested instruction in a repository.[^codex-agents]

Therefore the common rules live in each repository's concise `AGENTS.md`; detailed specifications live in proper docs. The four instruction files have different invariants, research triggers and validation expectations. We do not create nested instruction trees before actual runtime modules and their different commands exist. When such modules appear, add a small local file only for the additional scope. Restart/reload the harness as its installed version requires and inspect its context to confirm discovery; static file checks cannot certify a live session's loaded instructions.

User/global harness settings can still affect behavior. This setup does not overwrite them, select a model, turn on experimental features or install a network tool. An instruction file is useful guidance, not an OS sandbox or an executable authorization system.

## Sessions, subagents and repository ownership

Codex's subagent guidance identifies noisy exploration and intermediate logs as a reason to delegate bounded read-heavy work. It cautions that concurrent writing creates coordination overhead. A useful delegated result is a compact, source-linked conclusion rather than the entire tool transcript.[^codex-subagents]

Claude subagents have separate context and configurable tools/permissions. Built-in agent behavior can differ; important constraints belong in the actual brief rather than being assumed inherited. Claude agent teams are documented as experimental, with resumption and coordination limitations. We should not depend on them to maintain our only copy of task ownership.[^claude-subagents][^claude-teams]

Our recommendation is a temporary feature coordinator, one owner for each bounded component task, and a fresh reviewer for meaningful changes. Independent implementations use separate top-level sessions. Helpers investigate narrow questions, analyze logs or challenge a diff. A small fix can remain one session.

A temporary Claude-on-CBR and Codex-on-PIO split is reasonable when contracts are agreed and the tasks are independent. Nothing in the reviewed evidence establishes this as a superior permanent assignment. Cross-review adds another perspective, but correlated model errors remain possible. We measure whether reviewers find consequential defects rather than counting approvals.

Git worktrees provide separate working directories on branches within a repository. They share repository infrastructure; they are not separate machines. This is why our task record also names test resources and external effects, rather than treating a new worktree as full isolation.[^git-worktree]

## ECC: what it actually contains

ECC is broader than a collection of prompts. Its source contains install profiles, platform configurations, skills, agent definitions, hooks, session restoration, continuous learning, a memory interface and orchestration tooling. There are **seven** named install profiles in the inspected manifest: minimal, opencode, core, developer, security, research and full. The minimal profile omits the hook runtime, but still includes several modules; “minimal” does not mean one reviewed skill.[^ecc-profiles]

This breadth can be valuable for someone who wants an integrated personal setup. It also expands the material we would maintain and the settings that could conflict with our development agreement. Skill catalog size is not itself a measure of quality or of context use: systems may load descriptions up front and full skills on demand. We did not measure token overhead or execution latency for ECC.

The inspected root license is MIT. That is relevant to reviewing reuse, but we have adapted concepts in original prose here rather than copying source files into the products. Installing ECC would not select licenses for our repositories or settle the license obligations of every optional dependency.[^ecc-license]

## Adoption matrix

| ECC area | Assessment | Decision for this setup |
|---|---|---|
| Contract-first skill | Useful emphasis on one authoritative boundary artifact, compatibility and runtime validation | Adapt into the shared protocol-change workflow |
| Search-first skill | Useful for new architecture/dependency decisions; disproportionate for trivial edits | Use bounded research when it can change a decision |
| Verification loop | Useful categories, but generic commands and thresholds need correction | Use real repo-specific commands and concrete failure cases |
| Structured worktree handoff | Useful separation of task, output and status | Adopt a small versioned handoff template |
| Installer profiles and hook consent | Better than an opaque all-or-nothing install; still requires review of the chosen path | Keep as an option for a later isolated pilot |
| Reference Codex configuration | Includes runtime choices, notifications and external tools outside this task's needs | Do not copy into user/global settings |
| Tmux worktree orchestration | Useful source example; opinionated launcher and extra moving parts | Do not make it a v0.1 development dependency |
| Continuous learning and session memory | Interesting mechanisms; not a replacement for reviewed project decisions | Do not enable as shared architectural authority |
| ECC as PIO or CBR substrate | Different responsibilities and proof requirements | No product dependency selected |

## Contract-first: keep the principle, adapt rollout

ECC's contract-first skill is directly relevant: review the shared boundary before provider and consumer implementations diverge, and validate runtime data rather than relying only on a language type. Its treatment of untrusted schema descriptions is also useful: a contract file can contain text an agent should analyze rather than obey.[^ecc-contract]

Our adaptation makes the protocol owner a coordinator of affected needs, not a dictator of provider convenience. A feature record links a protocol change and its consumers. Compatible additive contracts may land first while consumers adopt independently. Breaking changes need migration or version/capability negotiation. There is no cross-repository atomic merge, so “all participants agree” cannot mean all four PRs must somehow merge simultaneously.

For example, packet creation, packet submission and confirmed delivery are distinct observations. A schema that uses one boolean for all three would make the UI misleading even if every repository type-checks. A distinguishing fixture is more useful than agreement on attractive field names.

## Installation and configuration: material side effects

The hook-consent implementation explicitly identifies possible capabilities including source formatting, command/process changes, transcript-derived LLM egress, MCP activity and persisted observations. Its readiness check rejects a plan materializing hooks without enabled consent; declining strips hook runtime operations. This is a positive design feature. It is not evidence that every installation channel or enabled hook has identical behavior.[^ecc-consent]

The inspected Codex reference configuration includes live web search, desktop notification configuration and several MCP command definitions. Some package invocations are unversioned or use `@latest`. Copying that file would therefore select more than repository writing guidance. Whether a given field works depends on the installed Codex build and configuration scope; this review did not execute it.[^ecc-config]

The legacy sync script describes and implements a path involving user-level configuration/instruction merging and global Git safety hooks. That scope is materially different from adding eight repository instruction files. We have not run it. A later pilot must identify the exact installation channel, preview planned changes and verify the applied diff; a marketing description of “Codex support” is not a configuration contract.[^ecc-sync]

These findings do not imply ECC is malicious. They explain why “install it and see” is the wrong first step for a multi-repository setup whose existing user settings should remain predictable.

## Worktree orchestration: useful mechanics, wrong default dependency

ECC's orchestrator creates named worktrees and tmux panes with task/handoff/status paths. The launcher at the pinned commit invokes `codex exec` with a hardcoded `gpt-5.4` model and a `yolo` profile. The reference profile sets approval policy to `never` with workspace-write sandboxing. The name does not mean unrestricted access to every resource; actual capability still depends on runtime sandbox/network configuration. Nevertheless it is not a neutral adoption of the user's existing model and permission policy.[^ecc-worker][^ecc-config]

The launcher also asks the worker not to spawn further agents. It manages handoff/status artifacts and records failure. Those are useful source examples, but a process exit code is not feature acceptance. Our reviewer and integration test remain necessary.

We can start normal sessions in ordinary worktrees without adopting tmux management, model pins or ECC status semantics. Only add a launcher when repeated manual setup is a measured bottleneck. Its task ownership, interrupted-run behavior, resource isolation and human intervention must then be explicitly tested.

## Memory: promising techniques with a different authority model

ECC's session-start source selects an exact worktree match, then allows a project-name fallback only for legacy summaries without worktree metadata. It returns no matching summary for a different explicit worktree. It also wraps restored content as historical reference and warns against re-executing stale instructions. A preliminary audit's claim of automatic cross-project summary injection was contradicted by this source and rejected.[^ecc-session]

That is a useful memory-design lesson for CBR: scope matching and the distinction between a remembered instruction and a current authorization must survive compaction. A summary saying “create the migration” cannot authorize recreating an effect after restart.

The continuous-learning-v2 skill documents project-scoped instincts and an observer configuration. The unified-memory skill documents scoped memory artifacts and cautions that target-harness routing is not authorization. These are relevant design references, not proof of superior recall or durable epistemic correctness.[^ecc-learning][^ecc-memory]

CBR's accepted responsibilities remain stronger and more specific: immutable source evidence, typed revisions, support/conflict relationships, temporal applicability, exact context bytes, bounded jobs and explicit gaps. ECC memory must not become an undocumented second authority for those concepts. During development, a learned preference may suggest an ADR; it cannot silently overwrite one.

A future selective pilot should test same-project legacy-name collisions, stale branch information, source corrections, instruction-like text in retrieved artifacts, and what is sent to external models. We do not assert these tests have already passed or failed.

## Verification: adapt before reuse

ECC's verification skill covers build, types, lint, tests and diff review. Some sample commands pipe output to `tail` or `head`; the build example does not establish `pipefail` itself. Executed as an independent snippet in a normal shell, a downstream command can obscure the producer's failing exit code. Its later type-check snippet includes `pipefail`, so it would be inaccurate to claim the skill never accounts for pipelines.[^ecc-verify]

The same skill suggests a universal 80% coverage target and grep-based “security” checks. We should not import those as product quality definitions. Coverage does not prove crash recovery; printing matching lines can expose sensitive text; a clean grep is not security validation. A fixed `HEAD~1` diff is also not necessarily the actual PR change.

Our concrete replacement is repo-specific commands, original exit status, retained evidence, an explicit base/head and failure cases appropriate to the affected contract. Initially the repositories only have documentation validation. Runtime checks must be added with their implementation, not fictionalized in `AGENTS.md`.

## Loom and the first integrated journey

The inspected Loom sources separate the shared simulated world from UI behavior. The UI exposes graph editing, stage grouping, depth controls, project/session/workflow navigation and inspectable disagreement between a selected worker-v2 direction and a worker-v1 observation. Its visible distinction between “result returned,” verification and applicability is important product input.

This makes the migration story a strong candidate for the first integration acceptance. It does not select the production scene renderer, persistence model or protocol fields. A large single browser coordinate space is an implementation of the mock, not a requirement that the product materialize every project object at once.

For development, keep UI interaction work running beside backend work. A small real inspector should consume actual packet and execution observations early. The large canvas can continue evolving independently against explicitly labeled fixtures. This protects the semantic zoom vision without letting polished simulation conceal missing backend behavior.

Local source evidence: `ui-explorations/06-loom/app.js` lines 1–9 identify the shared world; lines 50–77 explain the document and stage links; `ui-explorations/shared/world.js` begins by identifying the simulated world. These files remain in the design workspace and were not imported as production code. [UI architecture](../architecture/UI.md) is the public contract reference.

## Alternatives and evaluation plan

**Full ECC adoption now** could reduce setup effort if its defaults matched ours. We would also inherit a large configuration and hook review surface before we have one real product journey. Defer it.

**One giant agent session across all repositories** is simple initially, but retains too much working state in one chat and obscures ownership. Use a replaceable coordinator and bounded component sessions instead.

**Four permanently autonomous repository agents** may increase activity while slowing contract convergence and review. Start with two independent implementation owners, not a standing swarm.

**Sequential-only development** is reasonable for early ambiguous contracts or a small team with limited review capacity. Parallelize only after tasks can proceed without making incompatible boundary decisions. This remains a valid fallback, not a failure of the architecture.

Measure the workflow using comparable real tasks: accepted outcome, integration failures, missed constraints, review defects, fresh-session reconstruction time, total model/tool cost and human attention. Include cold-start preparation and failed attempts. Record harness versions, task difficulty and evaluator. A small pilot is directional evidence; do not advertise a general performance improvement from one successful task.

If trying ECC later, pin the exact source, select the minimum relevant assets, use isolated disposable configuration, inspect changes, and compare against the plain repository-instruction workflow. Avoid enabling automatic learning and external tools in the first comparison: changing many variables would prevent us from knowing what helped. Keep adoption only if its benefit exceeds setup, context and maintenance costs.

## Decisions and remaining uncertainty

**Selected development practice:** short instruction maps; shared versioned architecture; one accountable task owner; bounded delegation; fresh review for consequential changes; explicit protocol rollout; integration at recorded revisions; scoped autonomy; no self-development before usable v0.1.

**Selected ECC disposition:** adapt a few principles in original project-specific guidance; no bundle, global configuration, hook runtime, memory observer or launcher installed.

**Still to validate:** actual harness instruction loading in new sessions, review effectiveness, sensible task sizes, renderer/desktop stack, adapters and OS enforcement, storage/recovery implementation, CBR model/library choices, numerical budgets and downstream memory benefit. Public visibility is separate from choosing the repositories' own licenses.

The architecture is sufficiently defined to start bounded foundation work. It is not sufficiently proven to skip experiments or declare the product done.

## Sources

Official documentation was retrieved during this review; those pages can change. ECC links below are pinned to the inspected commit.

[^openai-harness]: OpenAI, [Harness engineering](https://openai.com/index/harness-engineering/), 11 February 2026. Primary experience report, not a controlled benchmark.
[^claude-large]: Anthropic, [Working with large codebases](https://code.claude.com/docs/en/large-codebases). Primary product guidance.
[^claude-memory]: Anthropic, [How Claude remembers your project](https://code.claude.com/docs/en/memory), especially imports and `AGENTS.md`.
[^codex-agents]: OpenAI, [Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md).
[^codex-subagents]: OpenAI, [Subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents).
[^claude-subagents]: Anthropic, [Create custom subagents](https://code.claude.com/docs/en/sub-agents).
[^claude-teams]: Anthropic, [Orchestrate teams of Claude Code sessions](https://code.claude.com/docs/en/agent-teams), experimental status and limitations.
[^reddit-one]: r/ClaudeAI, [Tips for developing large projects with Claude Code](https://www.reddit.com/r/ClaudeAI/comments/1ljv2kz/tips_for_developing_large_projects_with_claude/). Community experience.
[^reddit-two]: r/ClaudeAI, [How do you usually get around when starting big projects?](https://www.reddit.com/r/ClaudeAI/comments/1t7ta88/how_do_you_usually_get_around_when_starting_big/). Community experience.
[^git-worktree]: Git, [git-worktree documentation](https://git-scm.com/docs/git-worktree), description and details.
[^ecc-package]: ECC, [package.json](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/package.json).
[^ecc-license]: ECC, [LICENSE](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/LICENSE).
[^ecc-profiles]: ECC, [install profiles](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/manifests/install-profiles.json).
[^ecc-contract]: ECC, [contract-first skill](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/skills/contract-first/SKILL.md).
[^ecc-consent]: ECC, [hook consent implementation](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/scripts/lib/install/hook-consent.js), capability disclosure and `assertHookConsentReady`.
[^ecc-config]: ECC, [Codex reference configuration](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/.codex/config.toml).
[^ecc-sync]: ECC, [legacy Codex sync](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/scripts/sync-ecc-to-codex.sh).
[^ecc-worker]: ECC, [Codex worktree worker launcher](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/scripts/orchestrate-codex-worker.sh#L80) and [worktree orchestrator](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/scripts/lib/tmux-worktree-orchestrator.js).
[^ecc-session]: ECC, [session-start implementation](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/scripts/hooks/session-start.js#L277), matching at lines 277–322 and historical guard at lines 684–696.
[^ecc-learning]: ECC, [continuous-learning-v2 skill](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/skills/continuous-learning-v2/SKILL.md).
[^ecc-memory]: ECC, [unified-memory skill](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/skills/unified-memory/SKILL.md).
[^ecc-verify]: ECC, [verification-loop skill](https://github.com/affaan-m/ECC/blob/8321021c54d670126ce3b2969d5deb880b4b0c2a/skills/verification-loop/SKILL.md).
