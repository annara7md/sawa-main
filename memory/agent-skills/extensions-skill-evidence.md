# Extensions Skill Evidence

- scope: shared
- purpose: Preserve only confirmed local evidence for extension-related workflows and note unresolved gaps explicitly.
- read_when: Read before authoring or revising `skills/extensions-development/SKILL.md`.
- source_paths: `sawa-dashboard/src/extensions/`, `sawa-backend/saleor/graphql/app/`, `sawa-backend/saleor/app/`
- last_reviewed: 2026-03-14

## Confirmed Evidence

- `sawa-dashboard/src/extensions/` is a large analyzed frontend area with `components/`, `data/`, `domain/`, `hooks/`, `ripples/`, and many `views/`.
- Confirmed dashboard extension views include `ExploreExtensions`, `InstallCustomExtension`, `InstalledExtensions`, `AddCustomExtension`, `EditCustomExtension`, `EditCustomExtensionWebhook`, `EditPluginExtension`, `EditManifestExtension`, `EditManifestExtensionPermissions`, and `ViewManifestExtension`.
- Confirmed dashboard routes are split into `custom`, `app`, and `plugin` sections in `sawa-dashboard/src/extensions/urls.ts`, with explicit builders for installed/explore lists, custom app add/edit/webhook paths, manifest app view/edit/request-permissions paths, and plugin edit paths.
- Confirmed dashboard routes and tests reference app-specific paths such as `/extensions/app/<id>`, deep app subpaths like `/config` and `/settings/webhooks`, and legacy compatibility paths under `/apps/<id>/app`.
- `sawa-dashboard/src/extensions/domain/` contains local manifest parsing and validation for extension work. The analyzed schemas enforce mount/target compatibility, relative URL rules, and that extension permissions remain a subset of app permissions.
- `sawa-dashboard/src/extensions/views/InstallCustomExtension/hooks/useFetchManifest.ts` confirms that the dashboard calls backend `appFetchManifest`, maps backend `AppErrorCode` values into form errors, and treats manifest retrieval as a first-class install flow.
- `sawa-dashboard/src/extensions/views/ExploreExtensions/ExploreExtensions.tsx` confirms that extension discovery already includes a dedicated browse/search surface in the dashboard UI.
- `sawa-backend/saleor/graphql/app/` contains app and extension GraphQL schema, mutations, dataloaders, and tests.
- Confirmed backend query and benchmark coverage includes `appExtensions`, `appExtension`, and app-extension test files, including filter coverage by `targetName` and `mountName`.
- `sawa-backend/saleor/graphql/app/schema.py` explicitly exposes `app_extensions` and `app_extension` queries inside the app schema.
- `sawa-backend/saleor/graphql/app/types.py` confirms both manifest-backed extension data and persisted `AppExtension` records, including `label`, `url`, `mountName`, `targetName`, `settings`, `permissions`, and access-token resolution.
- `sawa-backend/saleor/app/models.py` confirms a persisted `AppExtension` model tied to `App`, with fields for `label`, `url`, `mount`, `target`, `permissions`, `http_target_method`, and JSON `settings`.
- `sawa-backend/saleor/app/installation_utils.py` contains confirmed manifest-driven extension installation logic using extension data such as `label`, `url`, `mount`, `target`, `settings/options`, and permissions.
- `sawa-backend/saleor/app/manifest_validations.py` confirms backend normalization and validation of extension `mount`, `target`, URLs, and permission scope before installation.
- `sawa-backend/saleor/app/app_manifest_sample.json` and `manifest_schema.py` confirm that app manifests currently include an `extensions` section.

## Open Gaps

- There is no existing root-level extension-development skill in this workspace.
- The current evidence confirms extension management surfaces and manifest-backed installation behavior, but it does not yet define a complete end-to-end authoring workflow that should be encoded as a root skill without further local analysis.
- The current evidence is stronger for extension discovery, installation, editing, and GraphQL exposure than for a full standalone extension-development lifecycle.

## Local Paths Reviewed

- `sawa-dashboard/src/extensions/`
- `sawa-dashboard/src/extensions/urls.test.ts`
- `sawa-dashboard/src/extensions/urls.ts`
- `sawa-dashboard/src/extensions/domain/app-manifest.ts`
- `sawa-dashboard/src/extensions/domain/app-extension-manifest.ts`
- `sawa-dashboard/src/extensions/domain/extension-manifest-validator.ts`
- `sawa-dashboard/src/extensions/views/ExploreExtensions/ExploreExtensions.tsx`
- `sawa-dashboard/src/extensions/views/InstallCustomExtension/hooks/useFetchManifest.ts`
- `sawa-backend/saleor/graphql/app/schema.py`
- `sawa-backend/saleor/graphql/app/types.py`
- `sawa-backend/saleor/graphql/app/tests/queries/test_app_extensions.py`
- `sawa-backend/saleor/graphql/app/tests/queries/test_app_extension.py`
- `sawa-backend/saleor/app/models.py`
- `sawa-backend/saleor/app/installation_utils.py`
- `sawa-backend/saleor/app/manifest_validations.py`
- `sawa-backend/saleor/app/app_manifest_sample.json`
- `sawa-backend/saleor/app/manifest_schema.py`
