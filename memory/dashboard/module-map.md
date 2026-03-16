# Dashboard Module Map

- scope: dashboard
- purpose: Map the highest-value frontend directories so agents can navigate `sawa-dashboard/src/` quickly.
- read_when: Read after architecture when choosing where to inspect or implement a frontend change.
- source_paths: `sawa-dashboard/src/channels/`, `sawa-dashboard/src/discounts/`, `sawa-dashboard/src/orders/`, `sawa-dashboard/src/products/`, `sawa-dashboard/src/components/`, `sawa-dashboard/src/graphql/`, `sawa-dashboard/src/hooks/`, `sawa-dashboard/src/utils/`
- last_reviewed: 2026-03-14

## Summary

- `sawa-dashboard/src/channels/`: channel configuration flows and related views, forms, and handlers
- `sawa-dashboard/src/discounts/`: discount, promotion, voucher, and sale-related frontend logic
- `sawa-dashboard/src/orders/`: order views and order-management UI flows
- `sawa-dashboard/src/products/`: product listing and product-management UI
- `sawa-dashboard/src/components/`: reusable UI components shared across feature modules
- `sawa-dashboard/src/graphql/`: generated types, hooks, and schema helpers
- `sawa-dashboard/src/hooks/`: reusable React hooks
- `sawa-dashboard/src/utils/`: shared utility helpers

Concrete structure from analysis:

- `sawa-dashboard/src/orders/` contains many specialized components plus `views/`, `containers/`, `fixtures/`, `hooks/`, `ripples/`, and `utils/`.
- `sawa-dashboard/src/discounts/` is split mainly across `components/`, `models/`, and `views/`.
- `sawa-dashboard/src/components/` contains especially dense shared subareas such as `ConditionalFilter`, `Datagrid`, `Sidebar`, `AppLayout`, and `ModalFilters`.

## Key Paths

- `sawa-dashboard/src/channels/`
- `sawa-dashboard/src/discounts/`
- `sawa-dashboard/src/orders/`
- `sawa-dashboard/src/products/`
- `sawa-dashboard/src/components/`
- `sawa-dashboard/src/graphql/`
- `sawa-dashboard/src/hooks/`
- `sawa-dashboard/src/utils/`
- `sawa-dashboard/src/orders/components/`
- `sawa-dashboard/src/orders/views/`
- `sawa-dashboard/src/discounts/components/`
- `sawa-dashboard/src/discounts/views/`
- `sawa-dashboard/src/components/ConditionalFilter/`
- `sawa-dashboard/src/components/Datagrid/`

## Rules and Patterns

- Start with the nearest feature directory before jumping into shared utilities.
- If a behavior spans multiple screens, check feature-local `views/`, `components/`, and related hook files together.
- If the code references GraphQL hooks, inspect `sawa-dashboard/src/graphql/` and feature-specific query files.

## Risks

- Shared UI components can hide business assumptions that only surface in specific feature modules.
- Feature modules often include tests, handlers, and utils nearby, so reading only the page component can give an incomplete picture.
