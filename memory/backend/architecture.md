# Backend Architecture

- scope: backend
- purpose: Summarize the high-level architecture and domain boundaries of `sawa-backend/`.
- read_when: Read first for any backend task, especially before touching GraphQL, transactions, or domain modules.
- source_paths: `sawa-backend/AGENTS.md`, `sawa-backend/README.md`, `sawa-backend/pyproject.toml`, `sawa-backend/saleor/`
- last_reviewed: 2026-03-14

## Summary

`sawa-backend/` is a Saleor-based headless commerce backend built with Django, GraphQL, PostgreSQL, Celery, and `uv`. It is organized around many domain modules under `sawa-backend/saleor/`, with `sawa-backend/saleor/graphql/` acting as the main API surface.

Important infrastructure layers include:

- `sawa-backend/saleor/graphql/` for schema, resolvers, mutations, and DataLoaders
- `sawa-backend/saleor/core/` for shared infrastructure
- `sawa-backend/saleor/asgi/` for ASGI server setup
- `sawa-backend/saleor/schedulers/` for scheduled background work

Analyzed file counts show that `sawa-backend/saleor/graphql/` is by far the largest backend area, followed by heavy business domains like `order`, `product`, `payment`, `checkout`, and `account`. In practice, many backend investigations start in `graphql/` and then drop into one of those owning domains.

## Key Paths

- `sawa-backend/saleor/graphql/`
- `sawa-backend/saleor/core/`
- `sawa-backend/saleor/asgi/`
- `sawa-backend/saleor/schedulers/`
- `sawa-backend/pyproject.toml`
- `sawa-backend/saleor/order/`
- `sawa-backend/saleor/product/`
- `sawa-backend/saleor/payment/`
- `sawa-backend/saleor/checkout/`

## Rules and Patterns

- Treat GraphQL behavior as an API contract with frontend consequences.
- Domain modules own business logic; use them to find the real source of behavior.
- Backend changes involving orders, checkout, vouchers, or payments deserve extra care around transactions and locking.

## Risks

- A change in GraphQL or domain logic can affect both internal correctness and dashboard behavior.
- Performance and integrity issues often hide in resolver data access or transaction boundaries.
