---
name: github-push-changes
description: >-
  Review, validate, commit, and push current repository changes to GitHub when
  explicitly requested. Do not use for Git advice, skill editing, or implementation
  without a push request.
---

# Push Current Changes to GitHub

A push request authorizes review, validation, staging, commit, and ordinary push.
Do not ask for permission again. Follow the target repository's `AGENTS.md`,
applicable nested instructions, and any referenced validation, cleanup, and
secret-handling guidelines.

1. **Inspect once.** Check status, staged and unstaged diffs, untracked files,
   branch, remote, and upstream. Review the entire requested scope, including
   pre-existing changes and outgoing commits. Use the specified destination or
   established upstream; ask only if the destination is unclear. Report excluded
   paths and reasons. Stop if outgoing commits contain secrets.
2. **Fetch and compare.** Fetch the target remote and check ahead/behind counts.
   Integrate remote changes only by fast-forward when the worktree permits it.
   On divergence or blocked integration, preserve the work and report the blocker;
   do not stash, merge, rebase, reset, or force push automatically.
3. **Validate once.** Select the checks required by the target repository for the publication
   scope. Reuse results covering the exact content; rerun only after relevant
   edits or failures. Fix failures caused by the changes. Leave the push pending
   if required checks remain blocked or failing, unless the user directs otherwise.
4. **Commit and push.** Stage reviewed paths explicitly, preserving staged work
   outside the scope. Inspect the staged diff and run `git diff --cached --check`.
   Commit descriptively without amending, then push only the intended branch.
   If no new changes exist, push outgoing commits without an empty commit.
   On rejection, inspect the remote state before proceeding. Do not bypass hooks,
   push unrelated refs, create a PR, or initiate deployment.
5. **Verify and report.** Fetch again, confirm zero ahead/behind against the target,
   and check remaining worktree changes. Report commit, remote branch, validation,
   and remaining or excluded changes. Distinguish Git publication from CI/deployment.

Keep reads targeted and outputs bounded. Do not reread unchanged instructions or
repeat completed checks; review the staged diff only for publication correctness.
