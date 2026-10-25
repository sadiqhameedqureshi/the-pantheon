---
description: Weekly or pre-release health check. Rewrites
  docs/maintenance-report.md.
model: haiku
---

Run each check and capture SUMMARIES only, never full logs:
1. npm audit: counts by severity.
2. npm outdated: packages one or more major versions behind.
3. grep TODO|FIXME in src: count, and any older than the last release.
4. Test suite: pass rate and coverage.
5. Lighthouse and bundle size vs. budgets in docs/conventions.md.
6. docs/backlog.md: P0/P1 bugs open more than 14 days.

Compare each figure with the previous docs/maintenance-report.md.
Rewrite the report: a table of figures with the change since last run,
then recommended actions ranked by risk.

Return (max 10 lines): the top 3 actions and anything that got worse.
