# Agent Skills Specification Analysis

- scope: shared
- purpose: Record the current structural requirements and constraints from the Agent Skills specification.
- read_when: Read before creating or validating any local `SKILL.md` or deciding whether supporting directories are needed.
- source_paths: `https://agentskills.io/specification`
- last_reviewed: 2026-03-14

## Summary

The current specification says a skill directory must contain `SKILL.md` and may also contain `scripts/`, `references/`, `assets/`, and additional files or directories. `SKILL.md` must contain YAML frontmatter followed by Markdown content.

Confirmed frontmatter fields currently documented include:

- required: `name`, `description`
- optional: `license`, `compatibility`, `metadata`, `allowed-tools`

The specification also documents constraints for `name` and `description`, including a 1024-character limit for `description`.

## Key Rules

- `name` is required and constrained in format.
- `description` is required and is explicitly used to describe what the skill does and when to use it.
- `scripts/`, `references/`, and `assets/` are optional, not mandatory.
- Progressive disclosure and file references are part of the formal model, not just authoring advice.

## Implications for Sawa Main

- Every local skill in `skills/*/SKILL.md` must have valid frontmatter and a bounded, intentional `description`.
- Optional directories should only be created when the analysis shows they add value.
- The local program can use optional fields like `allowed-tools` only when local evidence justifies them, as already seen in `sawa-dashboard/.claude/plugins/dashboard-playwright/skills/analyze-failures/SKILL.md`.

## Source URLs

- `https://agentskills.io/specification`
