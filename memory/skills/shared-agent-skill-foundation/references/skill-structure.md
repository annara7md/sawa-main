# Skill Structure

## Required Core

- every skill package must contain `SKILL.md`
- `SKILL.md` must keep valid frontmatter with only `name` and `description`
- supporting files should exist only when analysis shows they add value

## Supporting Material Rules

- add `references/` when the skill needs heavier material that should not always live inline
- add `scripts/` only when repeated helper work is stable enough to package
- add `HEARTBEAT.md` only when the skill has a recurring operational cadence

## Local Package Standard

- `skills/bankr-signals/` proves this workspace already uses multi-file skill packages
- `shared-agent-skill-foundation/` holds the cross-skill package rules for the root skills program
- domain skills should keep their own local references instead of relying only on one global reference directory

## Derived From

- `memory/agent-skills/specification.md`
- `memory/agent-skills/best-practices.md`
- `memory/agent-skills/repository-analysis.md`
- `memory/agent-skills/client-implementation.md`
- `memory/agent-skills/bankr-signals-package-analysis.md`
