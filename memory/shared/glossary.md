# Shared Glossary

- scope: shared
- purpose: Define common project terms so agents can read docs and code with less ambiguity.
- read_when: Read when the domain language is unclear or when switching between frontend and backend contexts.
- source_paths: `sawa-dashboard/AGENTS.md`, `sawa-backend/AGENTS.md`, `sawa-dashboard/docs/multi-schema.md`
- last_reviewed: 2026-03-14

## Summary

- `Dashboard`: the admin frontend in `sawa-dashboard/`, built with React, TypeScript, GraphQL, and Vite.
- `Backend`: the Saleor-based Django and GraphQL service in `sawa-backend/`.
- `GraphQL schema`: the contract that defines queries, mutations, and types the dashboard consumes.
- `Code generation`: the process that creates TypeScript hooks and types in `sawa-dashboard/src/graphql/`.
- `Domain module`: a backend area under `sawa-backend/saleor/` such as `account`, `product`, `checkout`, or `order`.
- `Channel`: a Saleor commerce configuration boundary used for pricing, language, currency, and operational settings.
- `Checkout`: the backend and frontend flow for cart and purchase progression.
- `Order`: the post-checkout lifecycle including payment, fulfillment, and returns.
- `Webhook`: backend infrastructure for outgoing or incoming event-driven integrations.
- `DataLoader`: backend GraphQL pattern used to avoid N+1 queries.

## Key Paths

- `sawa-dashboard/src/graphql/`
- `sawa-dashboard/src/channels/`
- `sawa-backend/saleor/channel/`
- `sawa-backend/saleor/checkout/`
- `sawa-backend/saleor/order/`
- `sawa-backend/saleor/webhook/`

## Rules and Patterns

- If a term appears in both frontend and backend, check whether it names a business concept or a code location.
- In this workspace, many frontend modules mirror backend domain concepts but are not implemented in the same way.

## Risks

- Terms like `schema`, `channel`, and `checkout` can refer to business behavior, GraphQL contracts, or specific directories depending on context.
