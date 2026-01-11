# Agent Scripts

This folder collects agent helpers so they are easy to reuse in other repos or share during onboarding. Treat these rules as final until overriden from a child repo's `AGENTS.md`

This is heavily inspired from [@steipete's Agent-scripts](https://github.com/steipete/agent-scripts/tree/main) and [@Dimillian's Public Skills repo](https://github.com/Dimillian/Skills).

## Syncing With Other Repos
- Treat this repo as the canonical mirror for the shared guardrail helpers. Whenever you edit `scripts/committer` or `scripts/docs-list.ts` in any repo, copy the change here and then back out to every other repo that carries the same helpers so they stay byte-identical.
- When someone says “sync agent scripts,” pull the latest changes here, ensure downstream repos have the pointer-style `AGENTS.MD`, copy any helper updates into place, and reconcile differences before moving on.
- Keep every file dependency-free and portable: the scripts must run in isolation across repos. Do not add `tsconfig` path aliases, shared source folders, inline tiny helpers or duplicate the minimum code needed so the mirror stays self-contained.

## Pointer-Style AGENTS
- Shared guardrail text now lives only inside this repo: `AGENTS.MD` (shared rules + tool list).
- Every consuming repo’s `AGENTS.MD` is should be reduced to the pointer line `READ ./Projects/agents/AGENTS.MD BEFORE ANYTHING (skip if missing).` Place repo-specific rules **after** that line if they’re truly needed.
- Do **not** copy the `[shared]` or `<tools>` blocks into other repos anymore. Instead, keep this repo updated and have downstream workspaces re-read `AGENTS.MD` when starting work.
- When updating the shared instructions, edit `agents/AGENTS.MD`, mirror the change into `~/AGENTS.MD` (Codex global), and let downstream repos continue referencing the pointer.

## Sync Expectations
- This repository is the canonical mirror for the guardrail helpers used in mcporter and other Sweetistics projects. Whenever you edit `scripts/committer`, `scripts/docs-list.ts`, or related guardrail files in another repo, copy the changes back here immediately (and vice versa) so the code stays byte-identical.
- When someone asks to “sync agent scripts,” update this repo, compare it against the active project, and reconcile differences in both directions before continuing.

## @xorforce Agent Instructions (pointer workflow)
- The only full copies of the guardrails are `agents/AGENTS.MD` and `~/AGENTS.MD`. Downstream repos should contain the pointer line plus any repo-local additions.
- During a sync sweep: pull latest `agents`, ensure each target repo’s `AGENTS.MD` contains the pointer line at the top, append any repo-local notes beneath it, and update the helper scripts as needed.
- If a repo needs custom instructions, clearly separate them from the pointer so future sweeps don’t overwrite local content.
- For submodules repeat the pointer check inside each subrepo, push those changes, then bump submodule SHAs in the parent repo.
