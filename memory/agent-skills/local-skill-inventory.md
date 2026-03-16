# Local Skill Inventory Analysis

- scope: shared
- purpose: Inventory and compare existing local skill-like artifacts before creating the new root skills program.
- read_when: Read before authoring local `SKILL.md` files so the new program preserves proven local patterns and accounts for visible inconsistencies.
- source_paths: `sawa-backend/skills/pytest-runner/SKILL.md`, `sawa-backend/skills/saleor-django-migration/SKILL.md`, `sawa-dashboard/.claude/skills/saleor-dashboard-styles/SKILL.md`, `sawa-dashboard/.claude/plugins/dashboard-playwright/skills/analyze-failures/SKILL.md`, `sawa-dashboard/AGENTS.md`, `sawa-backend/AGENTS.md`
- last_reviewed: 2026-03-14

## Summary

The current workspace already contains several skill-like patterns:

- narrow command-oriented backend skills such as `pytest-runner` and `saleor-django-migration`
- a dashboard styling skill with focused UI and CSS guidance
- a much larger Playwright failure-analysis skill with explicit phases, input handling, and delegation rules
- broad repository-level guidance in `sawa-dashboard/AGENTS.md` and `sawa-backend/AGENTS.md`

## Key Rules

- Existing local skills consistently use frontmatter with at least `name` and `description`.
- Local skills vary in length and strictness, but the strongest ones are explicit about scope and non-goals.
- The most procedural local skills rely on concrete commands and ordered workflows rather than generic advice.
- Some local skills already use richer metadata such as `argument-hint` and `allowed-tools`, showing that optional metadata is already part of local practice when justified.

## Implications for Sawa Main

- The new root skills program should preserve narrow scope and explicit workflows from the best local examples.
- `shared-agent-skill-foundation` should not duplicate `AGENTS.md`; it should route domain skills toward the right local memory and guidance.
- `dashboard-development` and `backend-development` can be more focused than the broad `AGENTS.md` files because the new program has root-level references and memory available.

## Source URLs

- `sawa-backend/skills/pytest-runner/SKILL.md`
- `sawa-backend/skills/saleor-django-migration/SKILL.md`
- `sawa-dashboard/.claude/skills/saleor-dashboard-styles/SKILL.md`
- `sawa-dashboard/.claude/plugins/dashboard-playwright/skills/analyze-failures/SKILL.md`
- `sawa-dashboard/AGENTS.md`
- `sawa-backend/AGENTS.md`
