# Team Conventions
Single source of truth. Agents read this once; agent prompts never repeat it.

## Code
- TypeScript strict, no `any`. Named exports, one component per file.
- Config only via env vars; every var listed in `.env.example`. No secrets in code.
- DB: parameterized queries / ORM only. Validate input with zod on every endpoint and form.
- Endpoints return: 2xx, 400 validation, 401/403 auth, 404, 500. Errors logged as structured JSON; never log passwords, tokens or PII.
- Every data view handles loading / error / empty / success.
- No `console.log`; no unresolved TODO/FIXME at merge.
- Frontend: Tailwind, React hooks only, API calls only via `src/lib/api.ts`, API base URL from env.
- Breakpoints: mobile <768, tablet 768–1024, desktop >1024. Design for 375px first.
- WCAG 2.1 AA: labels, keyboard access, visible focus, 4.5:1 contrast, 44px touch targets.

## Tests
- Unit tests beside source (`*.test.ts[x]`). Names describe behavior: "returns 401 when token missing".
- Factory functions for test data; isolated test DB; clean up after each test; no flaky tests.

## Budgets (enforced in CI — defined here only)
- Unit coverage ≥ 80%. PR pipeline < 5 min.
- Lighthouse: perf ≥ 80, a11y ≥ 90, best-practices ≥ 80, SEO ≥ 80.
- FCP < 1.5s, LCP < 2.5s. API p95 < 200ms CRUD, < 500ms aggregates.
- JS < 200KB gz, CSS < 50KB gz.

## Git
- Conventional commits: feat / fix / test / refactor / chore.
- `main` ← `develop` ← `feature/<track>`; hotfixes `hotfix/<BUG-id>` → `main`.

## Docs & IDs
- Every item has a greppable ID: features `F-01`, stories `US-001`, screens `SCR-01`, endpoints `EP-01`, tracks `T-A`, spec issues `SI-01`, bugs `BUG-001`, feature requests `FEAT-001`.
- Find what you need with Grep on IDs/headings; don't read whole docs unless your prompt says so.
- Spec problems go to `docs/spec-issues.md` — never silently "fix" a spec.

## Gate (run before reporting done)
`npm run lint && npm run typecheck && npm test`

## Handoff
Return to the orchestrator ≤ 10 lines: files written, counts, open issues. Never paste file contents back.
