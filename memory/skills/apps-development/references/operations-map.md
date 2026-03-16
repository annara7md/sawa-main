# Apps Operation Map

## Entry Operations

- direct app creation through management command and GraphQL mutation
- manifest fetch and validation through backend validation and fetch-manifest mutation
- manifest-based installation through CLI, GraphQL install mutation, async install task, and installation utilities

## Ongoing Management Operations

- queries for `appsInstallations`, `apps`, `app`, `appExtensions`, and `appExtension`
- mutations for update, delete, activate, deactivate, retry install, delete failed installation, token create/delete/verify, and app-problem flows

## Dashboard Touchpoints

- manifest fetch flow in `InstallCustomExtension`
- manifest app management in `EditManifestExtension`
- permission approval flow in `EditManifestExtensionPermissions`
- app iframe routing in `ViewManifestExtensionIframe`
- custom app management in `EditCustomExtension`

## Derived From

- `memory/agent-skills/apps-operation-map.md`
