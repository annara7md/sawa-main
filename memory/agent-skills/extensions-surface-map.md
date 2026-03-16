# Extensions Surface Map

- scope: shared
- purpose: Break down the confirmed extension-related surfaces into concrete dashboard and backend areas without assuming a full authoring lifecycle.
- read_when: Read after `memory/agent-skills/extensions-skill-evidence.md` when a task needs finer routing inside extension-related code.
- source_paths: `sawa-dashboard/src/extensions/views/`, `sawa-dashboard/src/extensions/components/`, `sawa-dashboard/src/extensions/domain/`, `sawa-dashboard/src/extensions/urls.ts`, `sawa-backend/saleor/app/models.py`, `sawa-backend/saleor/graphql/app/schema.py`
- last_reviewed: 2026-03-14

## Confirmed Dashboard Surface Groups

### Discovery and listing

- `ExploreExtensions` is a browse/search surface for extension discovery in `sawa-dashboard/src/extensions/views/ExploreExtensions/ExploreExtensions.tsx`.
- `InstalledExtensions` is the installed-extension list surface in `sawa-dashboard/src/extensions/views/InstalledExtensions/InstalledExtensions.tsx`.
- `InstalledExtensions` is tied to pending installations, failed-installation removal, and app-problem dismissal through `usePendingInstallation`, `useAppAllProblemsLazyQuery`, and `useAppProblemDismissMutation`.

### Custom app surfaces

- `AddCustomExtension` creates a custom app-style extension by collecting app name and permissions in `sawa-dashboard/src/extensions/views/AddCustomExtension/AddCustomExtension.tsx`.
- `InstallCustomExtension` has two confirmed entry modes in `sawa-dashboard/src/extensions/views/InstallCustomExtension/InstallCustomExtension.tsx`: from query-param manifest URL and from manual form entry.
- `EditCustomExtension` manages an existing custom app surface in `sawa-dashboard/src/extensions/views/EditCustomExtension/EditCustomApp.tsx`.
- `EditCustomExtension` is tied to app update, token create/delete, webhook delete, activate/deactivate, and delete flows.
- Dedicated webhook surfaces also exist: `AddCustomExtensionWebhook` and `EditCustomExtensionWebhook`.
- `AddCustomExtensionWebhook` creates webhooks for a chosen app by combining app lookup, available-event introspection, and `useWebhookCreateMutation`.
- `EditCustomExtensionWebhook` edits existing webhooks with `useWebhookDetailsQuery` and `useWebhookUpdateMutation`.
- `WebhookDetailsPage` is the shared webhook form surface and includes event selection, subscription query editing, permission alerting, and custom headers management.

### Manifest app surfaces

- `ViewManifestExtensionIframe` loads a manifest app page inside the dashboard in `sawa-dashboard/src/extensions/views/ViewManifestExtension/ViewManifestExtensionIframe.tsx`.
- The iframe view resolves dashboard URLs back into app URLs through `ExtensionsUrls.resolveAppCompleteUrlFromDashboardUrl(...)`.
- `EditManifestExtension` in `sawa-dashboard/src/extensions/views/EditManifestExtension/AppManageView.tsx` manages activation, deactivation, deletion, and the main app details page for manifest-backed apps.
- `EditManifestExtensionPermissions` is a dedicated approval/deny surface for requested app permissions in `sawa-dashboard/src/extensions/views/EditManifestExtensionPermissions/EditManifestExtensionPermissions.tsx`.

### Plugin surfaces

- `EditPluginExtension` in `sawa-dashboard/src/extensions/views/EditPluginExtension/EditPluginExtension.tsx` is a distinct configuration surface for plugins rather than app-manifest lifecycle management.
- The plugin surface handles plugin update mutations, channel-specific configuration selection, and secret-field editing/clearing dialogs.

### Shared extension infrastructure

- Shared dialogs exist for app activation, deactivation, and deletion under `sawa-dashboard/src/extensions/components/AppActivateDialog/`, `AppDeactivateDialog/`, and `AppDeleteDialog/`.
- `sawa-dashboard/src/extensions/components/AppAlerts/` is a separate alerting surface for app problems and failed webhook deliveries.
- `sawa-dashboard/src/extensions/components/AppExtensionContext/AppExtensionContextProvider.tsx` confirms popup-vs-deep-path activation behavior for app extensions.
- `sawa-dashboard/src/extensions/components/AppWidgets/AppWidgets.tsx` confirms rendered extension widgets are grouped by app and can execute through iframe GET, iframe POST, or non-iframe navigation depending on target and settings.
- `sawa-dashboard/src/extensions/handlers.ts` confirms webhook event selection is coupled to GraphQL subscription-query generation and mutation of the query AST.
- `sawa-dashboard/src/extensions/domain/` contains local parsing and validation rather than only UI helpers.

## Confirmed Route Structure

- `sawa-dashboard/src/extensions/urls.ts` defines three main route sections: `custom`, `app`, and `plugin`.
- The route layer confirms installed and explore lists, custom app add/edit/webhook routes, manifest app view/edit/request-permissions routes, and plugin edit routes.
- The route layer also includes backward-compatibility handling for legacy `/apps/<id>/app` navigation alongside `/extensions/app/<id>`.

## Confirmed Backend Surfaces Behind Extensions

- `sawa-backend/saleor/app/models.py` defines persisted `AppExtension` records tied to `App`.
- `sawa-backend/saleor/graphql/app/schema.py` exposes `appExtensions` and `appExtension`.
- `sawa-backend/saleor/graphql/app/types.py` resolves extension URL, mount, target, settings, permissions, and access token.
- `sawa-backend/saleor/app/installation_utils.py` creates extensions from manifest data during installation.
- `sawa-backend/saleor/app/manifest_validations.py` normalizes and validates extension URL, mount, target, and permission scope.

## What This Map Does Not Confirm

- It does not define a complete standalone extension-packaging workflow.
- It does not prove that plugin work and app-extension work are interchangeable.
- It does not define an external deployment lifecycle beyond the local management and GraphQL surfaces already visible.

## Local Paths Reviewed

- `sawa-dashboard/src/extensions/views/ExploreExtensions/ExploreExtensions.tsx`
- `sawa-dashboard/src/extensions/views/InstalledExtensions/InstalledExtensions.tsx`
- `sawa-dashboard/src/extensions/views/AddCustomExtension/AddCustomExtension.tsx`
- `sawa-dashboard/src/extensions/views/InstallCustomExtension/InstallCustomExtension.tsx`
- `sawa-dashboard/src/extensions/views/EditCustomExtension/EditCustomApp.tsx`
- `sawa-dashboard/src/extensions/views/AddCustomExtensionWebhook/AddCustomExtensionWebhook.tsx`
- `sawa-dashboard/src/extensions/views/EditCustomExtensionWebhook/EditCustomExtensionWebhook.tsx`
- `sawa-dashboard/src/extensions/views/EditManifestExtension/AppManageView.tsx`
- `sawa-dashboard/src/extensions/views/EditManifestExtensionPermissions/EditManifestExtensionPermissions.tsx`
- `sawa-dashboard/src/extensions/views/ViewManifestExtension/ViewManifestExtensionIframe.tsx`
- `sawa-dashboard/src/extensions/views/EditPluginExtension/EditPluginExtension.tsx`
- `sawa-dashboard/src/extensions/components/AppAlerts/useAppsAlert.ts`
- `sawa-dashboard/src/extensions/components/AppExtensionContext/AppExtensionContextProvider.tsx`
- `sawa-dashboard/src/extensions/components/WebhookDetailsPage/WebhookDetailsPage.tsx`
- `sawa-dashboard/src/extensions/components/AppWidgets/AppWidgets.tsx`
- `sawa-dashboard/src/extensions/domain/app-manifest.ts`
- `sawa-dashboard/src/extensions/domain/app-extension-manifest.ts`
- `sawa-dashboard/src/extensions/handlers.ts`
- `sawa-dashboard/src/extensions/urls.ts`
- `sawa-dashboard/src/extensions/urls.test.ts`
- `sawa-backend/saleor/app/models.py`
- `sawa-backend/saleor/app/installation_utils.py`
- `sawa-backend/saleor/app/manifest_validations.py`
- `sawa-backend/saleor/graphql/app/schema.py`
- `sawa-backend/saleor/graphql/app/types.py`
