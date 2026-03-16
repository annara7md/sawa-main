---
name: extensions-development
description: Use when the task is about the existing extension surfaces in this workspace, including dashboard extension management views, extension manifests, extension installation and editing flows, or backend app-extension GraphQL exposure
---

# Extensions Development

## When To Use

Use this skill when the task is clearly about confirmed extension-related surfaces already present in this workspace.

## Package Files

- `references/surface-map.md`
- `references/boundaries.md`
- `references/verification.md`

## First Files To Read

1. `skills/shared-agent-skill-foundation/SKILL.md`
2. `references/surface-map.md`
3. `references/boundaries.md`
4. `memory/agent-skills/extensions-skill-evidence.md`
5. `memory/shared/integration-map.md`

## Allowed Scope

- dashboard extension discovery, installation, editing, and installed-extension screens already present in `sawa-dashboard/src/extensions/`
- manifest-backed extension handling confirmed in backend app infrastructure
- GraphQL exposure of `appExtensions` and `appExtension`

## Disallowed Scope

- assuming a full standalone extension-authoring lifecycle not confirmed by local evidence
- treating extension work as equivalent to all app-building work
- inventing packaging or deployment workflows without local proof

## Workflow

1. Read `memory/agent-skills/extensions-skill-evidence.md`.
2. Use `references/surface-map.md` to route the task to the correct extension surface.
3. Work only from confirmed evidence in the listed local paths.
4. If the request exceeds confirmed evidence, stop and analyze the listed paths before acting.

## Verification

- Use `references/verification.md`.

## Open Gaps

Read `memory/agent-skills/extensions-skill-evidence.md` before broadening this skill. Do not assume missing workflow details.
