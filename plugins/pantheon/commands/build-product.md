---
description: Build a product from a one-line idea through 8 phases with
  3 approvals.
argument-hint: <product idea>
---

You are the orchestrator. Idea: $ARGUMENTS

## Your rules
- First check docs/conventions.md exists. If not, stop and ask the user
  to add it (Appendix B, or docs/conventions.md in the companion repo).
- Pass agents paths and IDs, never file contents. Do not read source
  files or whole documents yourself; grep for the line you need.
- Keep docs/progress.md: one line per phase (status, artifacts). If it
  already exists, resume from the first phase not marked done.
- At approvals be brief. Show only what is listed.
- Failures go only to the owning track's agent. Re-reviews check only
  the diff, by the reviewer that raised the issue. Max 2 fix loops,
  then stop and escalate with the open issues.

## 1 Discovery
janus QUESTIONS with the idea -> show the 5 questions in one message.
janus WRITE with idea + answers (relay follow-ups, max 2 rounds).
APPROVAL: show summary + OUT list. "Approve discovery? [yes/edit/redo]"

## 2 Spec & UX
thoth, then daedalus (sequential: daedalus needs the US- IDs).
APPROVAL: features, stories, screens, unmapped stories. "Approve specs?"

## 3 Architecture
athena.
APPROVAL: stack in one line + track graph. "Approve architecture?"

## 4 Scaffold
hermes SETUP. Show any MANUAL actions and wait until they are done.

## 5 Build
grep docs/implementation-plan.md for tracks and dependencies.
For each track whose dependencies are merged: create a git worktree on
feature/<track> and run vulcan or apollo (per owner) in it. Run
independent tracks in parallel. Open a PR to develop per track; merge when
CI passes. When all are merged, run the Gate on develop; send any failure
to the owning track's agent.

## 6 Test
nemesis FULL. Send each failure to its owning track's agent.

## 7 Review
minos and argus in parallel. BLOCKING items and HIGH/CRITICAL findings go
to the owning agent; then the flagging reviewer re-checks the diff only.
NEEDS-REWORK: stop and report to the user at once.

## 8 Deploy
hermes DEPLOY.

## Final report (max 10 lines)
Live URL; files created; test count and coverage; features shipped;
known issues (incl. open SI-); V2 items; repo URL.
