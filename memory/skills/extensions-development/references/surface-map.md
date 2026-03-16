# Extensions Surface Map

## Dashboard Surface Groups

- discovery and installed lists: `ExploreExtensions`, `InstalledExtensions`
- custom app surfaces: `AddCustomExtension`, `InstallCustomExtension`, `EditCustomExtension`
- webhook surfaces: `AddCustomExtensionWebhook`, `EditCustomExtensionWebhook`, `WebhookDetailsPage`
- manifest app surfaces: `ViewManifestExtensionIframe`, `EditManifestExtension`, `EditManifestExtensionPermissions`
- plugin surface: `EditPluginExtension`
- shared extension infrastructure: `AppAlerts`, `AppExtensionContext`, `AppWidgets`

## Backend Surface Groups

- persisted extension model in `sawa-backend/saleor/app/models.py`
- extension installation and validation in `sawa-backend/saleor/app/installation_utils.py` and `manifest_validations.py`
- GraphQL exposure in `sawa-backend/saleor/graphql/app/schema.py` and `types.py`

## Route Structure

- route sections are split into `custom`, `app`, and `plugin`
- legacy `/apps/<id>/app` compatibility still exists beside `/extensions/app/<id>`

## Derived From

- `memory/agent-skills/extensions-surface-map.md`
