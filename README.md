# The Pantheon

Companion files for the book **The Pantheon: How Eleven AI Agents Turn an Idea into Shipped Software** by Sadiq Abdul Hameed.

**Get the book on Amazon:** [Kindle](https://www.amazon.com/dp/B0HPJQNWWT) · [Hardcover](https://www.amazon.com/dp/B0HPMQM6RV)

Eleven Claude Code subagents, each named after a mythological figure whose domain matches its job, coordinated by three slash commands. Give it a one-line product idea, approve three times (discovery, specs, architecture), and the team builds, tests, reviews and ships an MVP.

| Agent | Job | Model |
|---|---|---|
| Janus | Validates the idea and scope | Sonnet |
| Thoth | Requirements and user stories | Sonnet |
| Daedalus | Screen specs (UX) | Sonnet |
| Athena | Architecture, API contract, parallel build tracks | Opus |
| Hermes | Repo, CI, branches, deploy | Sonnet |
| Vulcan | Backend, one track at a time | Sonnet |
| Apollo | Frontend, one track at a time | Sonnet |
| Nemesis | Integration, E2E, accessibility, performance tests | Sonnet |
| Minos | Code review and ship verdict (read-only) | Sonnet |
| Argus | Security audit (read-only) | Sonnet |
| Themis | Feedback triage into the backlog | Haiku |

Commands: `/build-product`, `/process-feedback`, `/maintenance-check`.

## Install

### Option 1: as a Claude Code plugin (recommended)

In Claude Code:

```text
/plugin marketplace add sadiqhameedqureshi/the-pantheon
/plugin install pantheon@the-pantheon
```

### Option 2: copy the files

Copy `plugins/pantheon/agents/*.md` into your project's `.claude/agents/` and `plugins/pantheon/commands/*.md` into `.claude/commands/`.

### Then, for either option

1. Copy [`docs/conventions.md`](docs/conventions.md) into your project's `docs/` folder and adjust it to your stack and budgets. Every agent reads it; `/build-product` stops if it is missing.
2. Install and sign in to the GitHub CLI (`gh`), and make sure Node.js is available.
3. Run:

```text
/build-product <your idea in two or three sentences>
```

## Example

```text
/build-product A tool for freelancers to track invoices and send automatic
polite reminders at 7, 14 and 30 days overdue. Dashboard shows outstanding
total and average days to payment. Single user, no payments processing in V1.
```

You can also call one agent directly:

```text
Use the argus agent to audit only the diff on this branch against develop.
```

## The four principles

1. **One owner per artifact.** Every document in `docs/` has exactly one author.
2. **One source of truth for rules.** Shared rules live in `docs/conventions.md`, not in agent prompts.
3. **ID-driven handoffs.** `US-001`, `SCR-01`, `EP-01`, `T-A`… Agents grep for IDs instead of reading whole documents.
4. **Short returns, small context.** Every agent returns at most 10 lines; the orchestrator passes paths and IDs, never file contents.

[The book](https://www.amazon.com/dp/B0HPJQNWWT) explains why each rule exists, walks through a complete build, and covers customising and troubleshooting the team.

## Caution

These agents generate and run code automatically. Review what they produce before it reaches real users or real data, especially authentication, payments and personal information.

## Licence

[MIT No Attribution](LICENSE). Copy, adapt and use these files freely.
