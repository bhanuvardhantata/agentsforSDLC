# GitHub Agent Guide

This repository includes GitHub-compatible custom agents under `.github/agents/` and supporting workflow guidance under the `.agent` folder. Use the custom agent that matches the task; each agent points back to the detailed workflow used by this repository.

## Custom agents

- `.github/agents/full-stack-developer.agent.md` — implement React, Express, and Prisma features
- `.github/agents/test-engineer.agent.md` — add and run focused Vitest and React Testing Library tests
- `.github/agents/database-engineer.agent.md` — evolve the Prisma schema, migrations, seed data, and API layer

## Workflow files

- `workflows/dev.md` — start the app, add features, and follow the app architecture
- `workflows/test.md` — run the test suite and add new component or hook tests
- `workflows/db.md` — set up PostgreSQL, run migrations, and seed demo data

## Source of truth

The root `AGENTS.md` file remains the repo-level compatibility guide for cross-platform AI tools. For GitHub agent workflows, prefer the custom agent prompt for the task, then use the detailed workflow files in `.agent/workflows/` and the commands in `package.json`.

## Project conventions

- Frontend: `src/client/`
- Backend: `src/server/`
- Database and Prisma: `prisma/`
- Setup scripts: `scripts/`
- Entry point: `src/server/index.js`

## Required workflow

When making code changes:

1. Read the relevant workflow file in `.agent/workflows/`
2. Follow the exact app scripts from `package.json`
3. Keep the architecture layered and consistent
4. Verify with the relevant test or build command before finishing

## Architecture rules

- Keep client pages focused on rendering and route-level composition
- Put data fetching in `src/client/hooks/` and service modules in `src/client/services/`
- Keep API logic in `src/server/routes/` and `src/server/services/`
- Keep Prisma models and migrations in `prisma/`
- Prefer existing conventions over creating ad hoc patterns

This folder is intended to make GitHub agent behavior predictable, repeatable, and aligned with the actual project structure.
