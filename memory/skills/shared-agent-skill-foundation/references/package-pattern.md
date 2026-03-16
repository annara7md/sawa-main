# Local Package Pattern

## Confirmed Example

- `skills/bankr-signals/` is a packaged local skill with `SKILL.md`, `HEARTBEAT.md`, `references/`, and `scripts/`

## What That Confirms

- this workspace already uses richer skill packages, not only single-file skills
- supporting files can be colocated under the skill package when they serve that skill directly

## What It Does Not Force

- not every skill needs `HEARTBEAT.md`
- not every skill needs `scripts/`
- support files should be justified by the analyzed scope of the skill

## Derived From

- `memory/agent-skills/bankr-signals-package-analysis.md`
