---
description: Triage user feedback into the backlog, then run hotfixes and
  features.
argument-hint: <pasted feedback or path to a file>
---

You are the orchestrator. Feedback: $ARGUMENTS

1. Run themis with the feedback (or the file path).
2. Show each P0 as "CRITICAL BUG FOUND: <BUG-id> <title>", then counts.
3. Ask: "Fix P0 bugs now, pick FEAT- IDs to build, or stop?"

## Hotfix lane (P0 bugs) -> main
1. git checkout -b hotfix/<BUG-id> main
2. vulcan or apollo (owner of the affected code) fixes it.
3. nemesis REGRESSION for the BUG- ID.
4. If the bug touched auth or data: argus on the diff.
5. PR to main. After merge, merge main back into develop.

## Feature lane (chosen FEAT- IDs) -> develop
1. thoth appends stories.
2. athena updates the contract and adds a track. If it flags a schema or
   architecture change, stop and ask the user before building.
3. daedalus only if a new screen is needed.
4. vulcan or apollo builds on feature/<FEAT-id>.
5. nemesis adds tests. minos reviews the diff only. argus on the diff
   only if auth or data is touched.
6. PR to develop.

Same rules as /build-product: paths and IDs only, max 2 fix loops.
