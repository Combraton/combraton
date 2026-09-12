# Session handoff

Template. A completed handoff is a dated observation; it does not authorize replaying old actions.

- **Task and timestamp:** issue link, owner and current state.
- **Goal and acceptance:** concise current objective, preserved constraints and reserved judgments.
- **Git state:** repository, branch, base/head commits, PR and uncommitted files; preserve unrelated changes.
- **Dependency state:** exact protocol and affected repository commits; relevant ADR/spec versions.
- **What changed:** meaningful behavior and files; decisions with authority/source, not merely chat recollections.
- **Evidence:** commands, environment, exit codes, artifact locations and tested revisions. Distinguish passed, failed, unavailable and not run.
- **What remains uncertain:** hypotheses, gaps, stale observations and required decisions.
- **Active resources:** processes, worktrees, test databases/ports, pending external effects and responsible owner; no credentials.
- **Next action:** one concrete step and its prerequisites; first reconcile this handoff with current Git/issues/runtime state.

Keep full raw logs outside the prompt and link useful excerpts to their source. Public artifacts must not expose private transcripts, secrets or personal machine paths. A summary of a summary is not a substitute for available source evidence.
