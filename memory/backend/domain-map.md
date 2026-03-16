# Backend Domain Map

- scope: backend
- purpose: Map the highest-value backend domains so agents can find the owning module faster.
- read_when: Read after architecture when choosing which backend module owns a behavior or bug.
- source_paths: `sawa-backend/saleor/graphql/`, `sawa-backend/saleor/account/`, `sawa-backend/saleor/product/`, `sawa-backend/saleor/checkout/`, `sawa-backend/saleor/order/`, `sawa-backend/saleor/payment/`, `sawa-backend/saleor/shipping/`, `sawa-backend/saleor/warehouse/`, `sawa-backend/saleor/plugins/`, `sawa-backend/saleor/webhook/`
- last_reviewed: 2026-03-14

## Summary

- `sawa-backend/saleor/graphql/`: API schema, resolvers, mutations, and DataLoaders
- `sawa-backend/saleor/account/`: user accounts, authentication, addresses
- `sawa-backend/saleor/product/`: catalog, product types, variants
- `sawa-backend/saleor/checkout/`: cart and checkout lifecycle
- `sawa-backend/saleor/order/`: order creation, fulfillment, returns, related flows
- `sawa-backend/saleor/payment/`: payment orchestration and gateway behavior
- `sawa-backend/saleor/shipping/`: shipping methods, zones, fulfillment-adjacent logic
- `sawa-backend/saleor/warehouse/`: stock and inventory
- `sawa-backend/saleor/plugins/`: plugin framework and integrations
- `sawa-backend/saleor/webhook/`: inbound and outbound webhook infrastructure

Within `sawa-backend/saleor/graphql/`, analyzed subtrees with the most files include:

- `sawa-backend/saleor/graphql/product/`
- `sawa-backend/saleor/graphql/account/`
- `sawa-backend/saleor/graphql/order/`
- `sawa-backend/saleor/graphql/discount/`
- `sawa-backend/saleor/graphql/checkout/`

The analyzed `product` GraphQL subtree also contains `bulk_mutations/`, `dataloaders/`, `filters/`, `mutations/`, `tests/`, and `types/`, while the `order` GraphQL subtree includes `bulk_mutations/`, `mutations/`, and a broad `tests/` tree with query, mutation, integration, benchmark, and deprecated coverage.

## Key Paths

- `sawa-backend/saleor/graphql/`
- `sawa-backend/saleor/account/`
- `sawa-backend/saleor/product/`
- `sawa-backend/saleor/checkout/`
- `sawa-backend/saleor/order/`
- `sawa-backend/saleor/payment/`
- `sawa-backend/saleor/shipping/`
- `sawa-backend/saleor/warehouse/`
- `sawa-backend/saleor/plugins/`
- `sawa-backend/saleor/webhook/`
- `sawa-backend/saleor/graphql/product/`
- `sawa-backend/saleor/graphql/order/`

## Rules and Patterns

- If the task starts from a mutation or resolver, trace from `sawa-backend/saleor/graphql/` into the owning domain module.
- Business concepts often span modules, but one module usually owns the core invariants.

## Risks

- The same user-visible behavior may traverse GraphQL, a domain module, plugin hooks, and background processing before it completes.
