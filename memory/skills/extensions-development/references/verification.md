# Extensions Verification

## Verify Against The Touched Surface

- route changes: verify the specific extension URL path or compatibility behavior touched
- manifest changes: verify the manifest fetch or validation path touched
- GraphQL changes: verify the `appExtensions` or `appExtension` surface touched
- webhook or widget changes: verify the specific surface rather than only the top-level list pages

## Verification Rule

Keep evidence gaps explicit if the touched flow extends beyond the confirmed local extension surfaces.

## Derived From

- `memory/agent-skills/extensions-skill-evidence.md`
- `memory/agent-skills/extensions-surface-map.md`
