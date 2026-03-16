# Backend Patterns

- scope: backend
- purpose: Record the backend coding patterns that are explicitly called out as important in local guidance.
- read_when: Read before editing backend mutations, resolvers, concurrency-sensitive flows, or input validation logic.
- source_paths: `sawa-backend/AGENTS.md`, `sawa-backend/saleor/graphql/`, `sawa-backend/saleor/core/`
- last_reviewed: 2026-03-14

## Summary

The backend guidance strongly emphasizes data integrity and GraphQL performance patterns.

## Key Paths

- `sawa-backend/saleor/graphql/`
- `sawa-backend/saleor/core/`
- `sawa-backend/saleor/order/`
- `sawa-backend/saleor/checkout/`
- `sawa-backend/saleor/payment/`

## Rules and Patterns

- Use atomic `F()` expressions instead of naive increment/decrement updates.
- Use `select_for_update()` when modifying critical rows that must be serialized.
- Keep critical checkout, order, and payment flows inside strong transaction boundaries.
- Use DataLoaders in GraphQL resolvers to avoid N+1 query patterns.
- Use Pydantic for complex nested input validation before persisting through Django ORM.

## Risks

- Ignoring these patterns can create race conditions, lock contention, or expensive GraphQL access patterns that are hard to diagnose later.
