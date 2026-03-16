# Apps Boundaries

## In Scope

- backend app domain work under `sawa-backend/saleor/app/`
- app GraphQL schema, dataloaders, mutations, and tests under `sawa-backend/saleor/graphql/app/`
- dashboard app-management surfaces already present under `sawa-dashboard/src/extensions/`

## Out Of Scope

- assuming a complete local app-authoring lifecycle that is not documented by confirmed evidence
- treating app work as identical to generic extension work
- inventing external packaging or deployment workflows without local support

## Escalate To Other Skills

- use `backend-development` when the task is backend-owned but not specifically app lifecycle work
- use `extensions-development` when the task is primarily about extension surfaces instead of full app operations
- use `dashboard-development` when the work is general dashboard UI behavior outside app lifecycle handling

## Derived From

- `memory/agent-skills/apps-skill-evidence.md`
- `memory/agent-skills/apps-operation-map.md`
