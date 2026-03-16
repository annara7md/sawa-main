# Memory Update Playbook

## When To Update

Update `memory/` when one of these happens:

- architecture or boundaries change in `sawa-dashboard/` or `sawa-backend/`
- developer commands, tooling, or setup instructions change
- a bug or regression reveals a repeated trap worth preserving
- cross-project integration points change, especially GraphQL schema and generated artifacts
- a task produces a durable engineering decision that future agents should know

## Update Checklist

1. Decide whether the change belongs in `shared`, `dashboard`, or `backend`.
2. Update the affected Markdown documents.
3. Update `memory/manifest.json` metadata and `last_updated` values.
4. Append a short note to `memory/change-log.md`.
5. Re-run JSON and structure verification commands before claiming the update is complete.

## Scope Rules

- Put cross-project knowledge only in `memory/shared/`.
- Put UI, frontend tooling, and feature-module details only in `memory/dashboard/`.
- Put Django, GraphQL backend, Celery, migration, and transaction details only in `memory/backend/`.
- Prefer links back to real source paths instead of copying long docs.

## Quality Rules

- Every scoped knowledge file must include `scope`, `purpose`, `read_when`, `source_paths`, and `last_reviewed`.
- Every scoped knowledge file must point to real workspace paths.
- Favor concise summaries and risk notes over duplicated documentation.
- If a fact is uncertain, say so explicitly or point the reader back to the source file.
