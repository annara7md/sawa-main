# Backend Integration Touchpoints

- scope: backend
- purpose: Show which backend areas most directly affect dashboard integration and generated frontend behavior.
- read_when: Read when a backend change may alter frontend GraphQL behavior or when a dashboard issue smells like a contract problem.
- source_paths: `sawa-backend/saleor/graphql/`, `sawa-backend/pyproject.toml`, `sawa-dashboard/docs/multi-schema.md`, `sawa-dashboard/src/graphql/`
- last_reviewed: 2026-03-14

## Summary

The most important backend integration touchpoint is `sawa-backend/saleor/graphql/`, because it defines the contract the dashboard consumes. When dashboard behavior changes unexpectedly after backend work, this is the first backend area to inspect, followed by the owning domain module.

Analysis of the GraphQL tree shows that contract-heavy backend areas are not evenly distributed. `product`, `account`, `order`, `discount`, and `checkout` are the densest analyzed GraphQL subtrees and are the most likely starting points when tracing dashboard-visible changes.

## Key Paths

- `sawa-backend/saleor/graphql/`
- `sawa-backend/saleor/product/`
- `sawa-backend/saleor/checkout/`
- `sawa-backend/saleor/order/`
- `sawa-dashboard/docs/multi-schema.md`
- `sawa-dashboard/src/graphql/`

## Rules and Patterns

- If a frontend query or mutation changes shape, start from backend GraphQL definitions.
- If the contract changed, verify whether dashboard codegen should be refreshed.
- Use the domain module that owns the business concept to inspect deeper behavior after checking the GraphQL surface.

## Risks

- Backend changes can appear harmless locally while still breaking generated dashboard hooks or assumptions about fields and behavior.
