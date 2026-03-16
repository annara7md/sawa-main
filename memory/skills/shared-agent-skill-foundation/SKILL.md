---
name: shared-agent-skill-foundation
description: Use when authoring, reviewing, or maintaining any root-level skill under sawa-main/skills/
---

# Shared Agent Skill Foundation

## Purpose

This skill provides the shared contract for the local `skills/` program. It exists to make every other root skill in `sawa-main/skills/` rely on analyzed sources instead of unsupported assumptions.

## Package Files

- `references/description-rules.md`
- `references/source-priority.md`
- `references/skill-structure.md`
- `references/evaluation-notes.md`
- `references/script-guidelines.md`
- `references/package-pattern.md`

## Required Source Order

Read sources in this order before changing or creating a root skill:

1. `memory/agent-skills/*.md`
2. `references/*.md`
3. The relevant domain evidence file such as `memory/agent-skills/dashboard-skill-evidence.md`
4. The relevant local project sources named by those files

## Scope Rules

- Use analyzed memory before generic advice.
- Prefer local project artifacts over broad ecosystem defaults.
- Keep skill scopes narrow enough for reliable triggering.
- Keep reusable root-skill guidance inside this package instead of scattering it across unrelated skill directories.

## Non-Goals

- Do not define dashboard-specific or backend-specific workflows here.
- Do not invent extension or app lifecycle details that the evidence files do not support.
- Do not treat this file as a substitute for the domain skills.

## How Child Skills Should Use This Package

- Use `references/description-rules.md` when writing or revising `description`.
- Use `references/source-priority.md` to decide which sources outrank others.
- Use `references/skill-structure.md` before adding `references/`, `scripts/`, or `HEARTBEAT.md`.
- Use `references/evaluation-notes.md` and `references/script-guidelines.md` when future work reaches evaluation or scripting.
- Use `references/package-pattern.md` when comparing a root skill package to the local `bankr-signals` example.
