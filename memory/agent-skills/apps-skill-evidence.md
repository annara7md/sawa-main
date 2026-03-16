# Apps Skill Evidence

- scope: shared
- purpose: Preserve only confirmed local evidence for app-related workflows and note unresolved gaps explicitly.
- read_when: Read before authoring or revising `skills/apps-development/SKILL.md`.
- source_paths: `sawa-dashboard/src/extensions/`, `sawa-backend/saleor/app/`, `sawa-backend/saleor/graphql/app/`, `sawa-backend/README.md`
- last_reviewed: 2026-03-14

## Confirmed Evidence

- The current Saleor-based workspace explicitly includes an `app` domain on the backend in `sawa-backend/saleor/app/`.
- `sawa-backend/saleor/app/models.py` confirms persisted backend app primitives: `App`, `AppToken`, `AppExtension`, `AppProblem`, and `AppInstallation`.
- `sawa-backend/saleor/app/management/commands/create_app.py` and `install_app.py` confirm local CLI-backed app creation and manifest-based installation flows already exist in this workspace.
- `sawa-backend/saleor/app/tasks.py` confirms asynchronous installation and removal flows, including `install_app_task` and cleanup of apps, tokens, extensions, webhooks, deliveries, and payloads for removed apps.
- `sawa-backend/saleor/app/installation_utils.py` confirms manifest fetch, manifest validation, app record creation, token exchange, brand-data fetch, and extension creation are part of the backend app lifecycle.
- `sawa-backend/saleor/app/manifest_validations.py` confirms backend validation for required Saleor version, permissions, unique identifiers, extension rules, and webhook structure.
- The backend GraphQL layer exposes a dedicated `saleor/graphql/app/` subtree with schema, filters, resolvers, dataloaders, mutations, and broad test coverage.
- `sawa-backend/saleor/graphql/app/schema.py` explicitly exposes `appsInstallations`, `apps`, `app`, `appExtensions`, and `appExtension`, plus mutations for app lifecycle, token lifecycle, installation retry/delete flows, manifest fetch, activation/deactivation, app problems, and re-enabling sync webhooks.
- `sawa-backend/saleor/graphql/app/mutations/app_fetch_manifest.py` confirms the backend has a dedicated manifest fetch-and-validate GraphQL mutation that returns normalized manifest data, permissions, extensions, webhooks, audience, author, and brand fields.
- Confirmed backend mutations include app creation, update, delete, install, retry install, fetch manifest, activation, deactivation, token operations, and app-problem flows.
- The dashboard extension area is already app-aware: route tests and views refer to app-specific screens, deep app paths, installation flows, and backward compatibility between `/extensions/app/...` and legacy `/apps/.../app` routes.
- `sawa-dashboard/src/extensions/domain/` contains app-manifest and app-extension-manifest validation logic, so app-related frontend handling is not just routing but includes typed manifest parsing and constraint checks.
- The upstream Saleor README identifies apps as a core extension mechanism for the dashboard.

## Open Gaps

- There is no existing root-level app-development skill in this workspace.
- The current evidence confirms app management, installation, tokens, and GraphQL/API exposure, but it does not yet document a complete local “build an app from scratch” lifecycle in one authoritative place.
- Because the strongest local evidence is split between dashboard extension screens and backend app infrastructure, the future app skill must explicitly tell the agent to analyze those sources before acting when the request goes beyond confirmed management flows.

## Local Paths Reviewed

- `sawa-dashboard/src/extensions/`
- `sawa-dashboard/src/extensions/urls.test.ts`
- `sawa-dashboard/src/extensions/urls.ts`
- `sawa-dashboard/src/extensions/domain/app-manifest.ts`
- `sawa-dashboard/src/extensions/domain/app-extension-manifest.ts`
- `sawa-dashboard/src/extensions/views/InstallCustomExtension/hooks/useFetchManifest.ts`
- `sawa-backend/saleor/app/`
- `sawa-backend/saleor/app/models.py`
- `sawa-backend/saleor/app/installation_utils.py`
- `sawa-backend/saleor/app/manifest_validations.py`
- `sawa-backend/saleor/app/tasks.py`
- `sawa-backend/saleor/app/management/commands/create_app.py`
- `sawa-backend/saleor/app/management/commands/install_app.py`
- `sawa-backend/saleor/graphql/app/`
- `sawa-backend/saleor/graphql/app/schema.py`
- `sawa-backend/saleor/graphql/app/types.py`
- `sawa-backend/saleor/graphql/app/mutations/app_fetch_manifest.py`
- `sawa-backend/saleor/graphql/app/tests/queries/test_app_extensions.py`
- `sawa-backend/README.md`
