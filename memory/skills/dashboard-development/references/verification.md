# Dashboard Verification

## Primary Commands

- `pnpm run test:quiet <file_path>` for focused tests
- `pnpm run check-types` for TypeScript verification
- `pnpm run lint` for linting
- `pnpm run generate` after GraphQL query or schema contract changes

## Verification Rules

- match the command to the specific change scope
- treat generated GraphQL files as outputs, not the primary source of truth
- re-check `memory/dashboard/risks.md` before claiming completion on broad shared-component changes

## Derived From

- `memory/dashboard/commands.md`
- `memory/dashboard/risks.md`
