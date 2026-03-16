# Workspace Memory

## What This Is

`memory/` is a workspace-level knowledge layer for `sawa-main/`. It helps agents and humans orient themselves quickly across `sawa-dashboard/` and `sawa-backend/` without re-discovering the project from scratch every time.

The source of truth is still the real code and project-local docs. This folder exists to summarize, route, and warn.

## How To Use It

1. Start here.
2. Decide whether the task is `shared`, `dashboard`, or `backend`.
3. Read the relevant architecture and commands documents first.
4. Read map, patterns, and risks before changing complex code.
5. Follow `source_paths` back into the real workspace.

## Reading Paths

### Shared or cross-project work

- Start with `memory/shared/overview.md`
- Then read `memory/shared/integration-map.md`
- Use `memory/shared/workflows.md` if the task crosses frontend/backend boundaries
- Use `memory/shared/glossary.md` if the terminology is unclear

### Dashboard-only work

- Start with `memory/dashboard/architecture.md`
- Then read `memory/dashboard/commands.md`
- Then read `memory/dashboard/module-map.md`
- Read `memory/dashboard/patterns.md` and `memory/dashboard/risks.md` before implementation

### Backend-only work

- Start with `memory/backend/architecture.md`
- Then read `memory/backend/commands.md`
- Then read `memory/backend/domain-map.md`
- Read `memory/backend/patterns.md` and `memory/backend/risks.md` before implementation

## File Map

- `memory/shared/`: workspace-wide context and integration guidance
- `memory/dashboard/`: frontend-specific knowledge for `sawa-dashboard/`
- `memory/backend/`: backend-specific knowledge for `sawa-backend/`
- `memory/agent-skills/`: analyzed external and local evidence for the Agent Skills program
- `memory/templates/`: reusable templates for future memory updates
- `memory/manifest.json`: machine-readable index of the memory system
- `memory/update-playbook.md`: rules for maintaining this folder
- `memory/change-log.md`: audit trail for memory changes
