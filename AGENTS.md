# AGENTS.md — AI Agent Instructions

## Overview

**simple-vite-react-express** is a production-ready full-stack starter template for React + Express + PostgreSQL.

**Goal**: Keep this project simple, maintainable, and easy for AI coding agents to follow without breaking the layered architecture.

This repo also includes a GitHub-focused workflow under `.agent/` for agent-based contributions. Use the root `AGENTS.md` as the cross-platform source of truth and the `.agent/workflows/*.md` files as the task-specific workflow guide.

## Architecture

```
Client (React 19 + MUI 7) → API Layer (Express 5) → Database (PostgreSQL via Prisma 7)
```

The codebase follows a layered pattern on both sides:

- **Client**: Pages → Hooks → Services → Axios → Server API
- **Server**: Routes → Services → Prisma → PostgreSQL

## Setup

```bash
nvm use                   # Node 22
npm install               # Install dependencies
cp example.env .env       # Create env file and set DATABASE_URL
npm run setup             # Interactive setup wizard
npm run db:setup          # Prisma migrate + generate
npm run db:seed           # Optional: seed sample data
npm run dev               # Start client and server concurrently
```

## Coding Conventions

- **ESM only** — `import`/`export`, no `require()`
- **No TypeScript** — use JSDoc for type hints
- **Functional components** — no class components
- **Custom hooks for data** — never call axios directly from pages
- **Service layer** — all API calls go through `src/client/services/`
- **MUI for UI** — use `@mui/material` components, `sx` prop for styling
- **Express 5** — async route handlers, no callback pattern

## Testing

```bash
npm test              # Watch mode
npm run test:run      # Single run (CI)
npm run test:coverage # Coverage report
```

- Framework: Vitest 4 + React Testing Library
- Test files: `src/client/__tests__/`
- Setup file: `src/client/__tests__/setup.js`
- For workflow guidance, see `.agent/workflows/test.md`

## Linting & Formatting

```bash
npm run lint          # Check
npm run lint:fix      # Auto-fix
npm run format        # Prettier
npm run format:check  # Check formatting
```

- ESLint 9 flat config (`eslint.config.js`)
- Prettier config (`.prettierrc`)
- Use the existing scripts rather than inventing new commands

## Commit Style

Use conventional commits: `feat:`, `fix:`, `chore:`, `docs:`, `style:`, `refactor:`, `test:`

## Workflow Files

- `.agent/README.md` — overview of the GitHub agent workflow
- `.agent/workflows/dev.md` — start app and add features
- `.agent/workflows/test.md` — run and add tests
- `.agent/workflows/db.md` — database and Prisma workflow

## Key Files

| File | Purpose |
|------|---------|
| `src/server/index.js` | Express server entry point |
| `src/client/index.jsx` | React app entry with routing |
| `src/client/services/` | API service layer |
| `src/client/hooks/` | Client-side data hooks |
| `prisma/schema.prisma` | Database schema |
| `prisma.config.ts` | Prisma CLI configuration |
| `vite.config.js` | Vite build configuration |
| `vitest.config.js` | Test configuration |
| `eslint.config.js` | Linting rules |
