# Apps Operation Map

- scope: shared
- purpose: Record the confirmed backend app lifecycle operations and the dashboard touchpoints that already exist in this workspace.
- read_when: Read after `memory/agent-skills/apps-skill-evidence.md` when a task needs finer routing across app creation, installation, token, permission, or manifest flows.
- source_paths: `sawa-backend/saleor/app/`, `sawa-backend/saleor/graphql/app/`, `sawa-dashboard/src/extensions/views/`, `sawa-dashboard/src/extensions/urls.ts`
- last_reviewed: 2026-03-14

## Confirmed Backend Domain Objects

- `sawa-backend/saleor/app/models.py` defines `App`, `AppToken`, `AppExtension`, `AppProblem`, and `AppInstallation`.
- `App` stores identity, permissions, URLs, manifest metadata, activation state, installation state, audience, author, and brand logo fields.
- `AppToken` stores hashed auth tokens and the last four characters.
- `AppInstallation` represents an installation job rather than an already-installed app.
- `AppProblem` records repeated or critical app problems and dismissal state.

## Confirmed Entry Operations

### Direct app creation

- `sawa-backend/saleor/app/management/commands/create_app.py` creates an app directly, assigns permissions, generates a default token, and can optionally POST the token to a target URL.
- `sawa-backend/saleor/graphql/app/mutations/app_create.py` creates an app through GraphQL, assigns permissions, generates a default token, and emits an installed webhook event.

### Manifest fetch and validation

- `sawa-backend/saleor/graphql/app/mutations/app_fetch_manifest.py` fetches and validates manifest data before installation.
- `sawa-backend/saleor/app/manifest_validations.py` validates required Saleor version, app permissions, unique identifier constraints, extensions, and webhooks.

### Manifest-based installation

- `sawa-backend/saleor/app/management/commands/install_app.py` performs manifest-based installation from the CLI.
- `sawa-backend/saleor/graphql/app/mutations/app_install.py` creates an `AppInstallation` record and delegates the actual install work to `install_app_task`.
- `sawa-backend/saleor/app/tasks.py` confirms installation is executed asynchronously through `install_app_task`.
- `sawa-backend/saleor/app/installation_utils.py` fetches the manifest, validates it, creates the `App`, applies permissions, creates extensions, and handles token delivery/brand data.

## Confirmed Ongoing Management Operations

- `sawa-backend/saleor/graphql/app/schema.py` exposes ongoing management queries for `appsInstallations`, `apps`, `app`, `appExtensions`, and `appExtension`.
- The same schema exposes lifecycle mutations for update, delete, activate, deactivate, retry install, delete failed installation, token create/delete/verify, problem create/dismiss, and re-enabling sync webhooks.
- File presence and test coverage confirm these operations in `sawa-backend/saleor/graphql/app/mutations/` and `sawa-backend/saleor/graphql/app/tests/mutations/`.
- `sawa-backend/saleor/graphql/app/mutations/app_update.py` restricts updates to allowed managers and supports permission updates.
- `sawa-backend/saleor/graphql/app/mutations/app_token_create.py` creates new app tokens with scope checks against the target app.

## Confirmed Background and Cleanup Operations

- `sawa-backend/saleor/app/tasks.py` removes old apps marked for deletion through `remove_apps_task`.
- That cleanup flow also removes related webhooks, deliveries, payloads, tokens, and extensions.
- `sawa-backend/saleor/app/tasks.py` records failed install status and error messages on `AppInstallation`.

## Confirmed Dashboard Touchpoints

- `sawa-dashboard/src/extensions/views/InstallCustomExtension/hooks/useFetchManifest.ts` calls backend `appFetchManifest` and maps backend `AppErrorCode` values into form errors.
- `sawa-dashboard/src/extensions/views/EditManifestExtension/AppManageView.tsx` manages app activation, deactivation, deletion, and app detail display for manifest-backed apps.
- `sawa-dashboard/src/extensions/views/ViewManifestExtension/ViewManifestExtensionIframe.tsx` mounts an app page inside the dashboard and translates dashboard URLs into app URLs.
- `sawa-dashboard/src/extensions/views/EditManifestExtensionPermissions/EditManifestExtensionPermissions.tsx` handles permission approval and denial flows for requested app permissions.
- `sawa-dashboard/src/extensions/views/EditCustomExtension/EditCustomApp.tsx` manages custom app update, token, webhook, activation, deactivation, and deletion flows.
- `sawa-dashboard/src/extensions/urls.ts` confirms app-related dashboard routing and compatibility with older `/apps/.../app` paths.

## What This Map Does Not Confirm

- It does not prove a single documented local workflow for building a brand-new external app from scratch outside these management surfaces.
- It does not define packaging, hosting, or deployment steps for third-party app code.
- It does not collapse plugin editing into the same lifecycle as app installation and app-manifest handling.

## Local Paths Reviewed

- `sawa-backend/saleor/app/models.py`
- `sawa-backend/saleor/app/installation_utils.py`
- `sawa-backend/saleor/app/manifest_validations.py`
- `sawa-backend/saleor/app/tasks.py`
- `sawa-backend/saleor/app/management/commands/create_app.py`
- `sawa-backend/saleor/app/management/commands/install_app.py`
- `sawa-backend/saleor/graphql/app/schema.py`
- `sawa-backend/saleor/graphql/app/types.py`
- `sawa-backend/saleor/graphql/app/mutations/app_create.py`
- `sawa-backend/saleor/graphql/app/mutations/app_install.py`
- `sawa-backend/saleor/graphql/app/mutations/app_update.py`
- `sawa-backend/saleor/graphql/app/mutations/app_token_create.py`
- `sawa-backend/saleor/graphql/app/mutations/app_fetch_manifest.py`
- `sawa-backend/saleor/graphql/app/tests/mutations/test_app_create.py`
- `sawa-backend/saleor/graphql/app/tests/mutations/test_app_install.py`
- `sawa-backend/saleor/graphql/app/tests/mutations/test_app_update.py`
- `sawa-backend/saleor/graphql/app/tests/mutations/test_app_token_create.py`
- `sawa-dashboard/src/extensions/views/InstallCustomExtension/hooks/useFetchManifest.ts`
- `sawa-dashboard/src/extensions/views/EditManifestExtension/AppManageView.tsx`
- `sawa-dashboard/src/extensions/views/EditManifestExtensionPermissions/EditManifestExtensionPermissions.tsx`
- `sawa-dashboard/src/extensions/views/ViewManifestExtension/ViewManifestExtensionIframe.tsx`
- `sawa-dashboard/src/extensions/views/EditCustomExtension/EditCustomApp.tsx`
- `sawa-dashboard/src/extensions/urls.ts`
