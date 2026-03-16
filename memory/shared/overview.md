# Shared Overview

- scope: shared
- purpose: Explain what lives in `sawa-main/`, what each project is responsible for, and how to decide the task scope quickly.
- read_when: Read first for any task that might span both projects or when the workspace structure is still unclear.
- source_paths: `sawa-dashboard/AGENTS.md`, `sawa-dashboard/README.md`, `sawa-backend/AGENTS.md`, `sawa-backend/README.md`
- last_reviewed: 2026-03-14

## Summary

`sawa-main/` currently contains two large codebases that work together but evolve independently:

- `sawa-dashboard/` is the admin frontend. It is a Saleor Dashboard-based React and TypeScript application that talks to GraphQL and depends on generated frontend artifacts.
- `sawa-backend/` is the headless commerce backend. It is a Saleor-based Django, GraphQL, and Celery application organized around many domain modules under `sawa-backend/saleor/`.

Use `dashboard` scope when the task is mainly about UI behavior, frontend routing, forms, generated hooks, or browser-visible behavior. Use `backend` scope when the task touches Django models, GraphQL resolvers, transactions, background jobs, or migrations. Use `shared` scope when the task crosses the GraphQL contract or when it is not obvious which side is the source of truth.

Workspace analysis shows clear density hotspots:

- In `sawa-dashboard/src/`, the largest analyzed areas by file count are `components`, `orders`, `extensions`, `discounts`, and `products`.
- In `sawa-backend/saleor/`, the largest analyzed areas by Python file count are `graphql`, `order`, `product`, `payment`, `checkout`, `account`, and `plugins`.

## Key Paths

- `sawa-dashboard/src/`
- `sawa-dashboard/docs/`
- `sawa-dashboard/package.json`
- `sawa-backend/saleor/`
- `sawa-backend/pyproject.toml`
- `sawa-backend/AGENTS.md`

## Rules and Patterns

- Start with architecture and commands before opening deep source files.
- Treat the GraphQL boundary as the main shared contract between the two projects.
- Prefer project-local docs for detailed commands, and use `memory/` to find the right document quickly.

## Risks

- Mixing frontend and backend reasoning too early can hide the real source of a bug.
- Changes to schema or generated files can appear as frontend issues even when the cause is backend-side.
