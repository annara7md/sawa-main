# Backend Risks

- scope: backend
- purpose: Highlight the backend failure modes most likely to cause integrity, performance, or operational problems.
- read_when: Read before changing checkout, order, payment, GraphQL, or migration-related code.
- source_paths: `sawa-backend/AGENTS.md`, `sawa-backend/saleor/order/`, `sawa-backend/saleor/checkout/`, `sawa-backend/saleor/payment/`, `sawa-backend/saleor/graphql/`
- last_reviewed: 2026-03-14

## Summary

The backend has several high-risk zones: concurrency-sensitive entities, GraphQL resolver performance, data migrations, and any flow that relies on background processing.

Analysis adds one more practical signal: the heaviest backend surface area sits in `sawa-backend/saleor/graphql/`, especially under `product/`, `account/`, `order/`, `discount/`, and `checkout/`. Changes there are both behavior-heavy and integration-heavy.

## Key Paths

- `sawa-backend/saleor/order/`
- `sawa-backend/saleor/checkout/`
- `sawa-backend/saleor/payment/`
- `sawa-backend/saleor/graphql/`
- `sawa-backend/saleor/*/migrations/`
- `sawa-backend/saleor/graphql/product/`
- `sawa-backend/saleor/graphql/order/`

## Rules and Patterns

- Do not modify historical migration files.
- Treat resolver query access as a performance risk until proven otherwise.
- Be deliberate about transaction boundaries in order and checkout flows.
- Treat large GraphQL subtrees with extensive test layouts as high-change-complexity areas.

## Risks

- Race conditions around orders, checkouts, or vouchers can produce hard-to-repair data issues.
- N+1 query regressions may only show up under realistic list sizes.
- Heavy synchronous data migrations can lock tables and create operational instability.
- Wide GraphQL areas with benchmark, integration, and deprecated test coverage usually indicate behavior with many compatibility edges.
