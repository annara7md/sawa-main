# Bankr Signals Package Analysis

- scope: shared
- purpose: Record the concrete local skill-package pattern implemented by `skills/bankr-signals/` and compare it to the current root skills structure without guessing about future changes.
- read_when: Read before treating `SKILL.md` alone as the full local standard for root skills in this workspace.
- source_paths: `skills/bankr-signals/`, `skills/shared-agent-skill-foundation/`, `skills/dashboard-development/`, `skills/backend-development/`, `skills/extensions-development/`, `skills/apps-development/`, `/Users/fahmifareed/.codex/skills/superpowers/writing-skills/SKILL.md`
- last_reviewed: 2026-03-14

## Confirmed `bankr-signals` Package Shape

- `skills/bankr-signals/` is not a single-file skill. It is a packaged skill directory with multiple operational layers.
- The package currently contains:
  - `skills/bankr-signals/SKILL.md`
  - `skills/bankr-signals/HEARTBEAT.md`
  - `skills/bankr-signals/references/api-reference.md`
  - `skills/bankr-signals/scripts/publish-signal.sh`
- The main `SKILL.md` acts as the entrypoint and links outward to operational and technical details.
- `HEARTBEAT.md` is a recurring operational checklist rather than general background prose.
- `references/api-reference.md` isolates heavier API detail outside the main skill body.
- `scripts/publish-signal.sh` provides a reusable execution artifact rather than only documenting shell commands inline.

## Confirmed Functional Layering Inside `bankr-signals`

### Main skill layer

- `skills/bankr-signals/SKILL.md` contains the top-level trigger description, integration workflow, endpoint overview, and links to supporting artifacts.
- The file mixes usage entrypoints, onboarding instructions, and API summary, but still delegates heavier reference and executable behavior to sibling files.

### Operational loop layer

- `skills/bankr-signals/HEARTBEAT.md` defines a periodic cadence with publish, close, poll, discover, and report routines.
- This makes the package suitable for recurring agent execution, not just one-off lookup.

### Reference layer

- `skills/bankr-signals/references/api-reference.md` provides endpoint, schema, and error details in a separate reference document.
- The reference file is clearly narrower and more technical than the main `SKILL.md`.

### Script layer

- `skills/bankr-signals/scripts/publish-signal.sh` automates one repeated write-path instead of leaving it as documentation only.
- The script has explicit environment and argument requirements and performs message signing plus API submission.

## Confirmed Local Standard From `writing-skills`

- `/Users/fahmifareed/.codex/skills/superpowers/writing-skills/SKILL.md` confirms the minimum skill structure is `skills/<skill-name>/SKILL.md`.
- The same document explicitly allows additional supporting files when needed, especially for heavy reference and reusable tools.
- Therefore, the local authoring guidance and the observed `bankr-signals` package are compatible: `SKILL.md` is the minimum, while `references/`, `scripts/`, and other support files are optional but valid when justified.

## Confirmed Structure Of Current Root Skills

- `skills/shared-agent-skill-foundation/` now contains `SKILL.md` plus a local `references/` directory for cross-skill package rules.
- `skills/dashboard-development/` now contains `SKILL.md` plus a local `references/` directory.
- `skills/backend-development/` now contains `SKILL.md` plus a local `references/` directory.
- `skills/extensions-development/` now contains `SKILL.md` plus a local `references/` directory.
- `skills/apps-development/` now contains `SKILL.md` plus a local `references/` directory.
- The current root skills no longer rely on one separate global `skills/references/` directory.

## Confirmed Structural Difference

- `bankr-signals` is a self-contained skill package with its own local support files.
- The current root skills now follow the same package-local `references/` pattern.
- The remaining difference is functional depth, not directory shape:
  - `bankr-signals` includes `HEARTBEAT.md`
  - `bankr-signals` includes a packaged `scripts/` helper
  - the current root skills still rely on analyzed workspace evidence in `memory/agent-skills/` and have not added heartbeat or scripts where no repeated operational need has been confirmed

## What This Analysis Confirms

- The workspace already contains at least one concrete example of a multi-file packaged skill under `skills/`.
- A local pattern exists for adding `HEARTBEAT.md`, `references/`, and `scripts/` under an individual skill directory.
- The root skills now mirror the package-local `references/` aspect of that shape.

## What This Analysis Does Not Confirm

- It does not prove that every skill in this workspace must include `HEARTBEAT.md`.
- It does not prove that every skill must contain a local `references/` or `scripts/` directory regardless of need.
- It does not by itself determine which support files each root skill should gain next.

## Local Paths Reviewed

- `skills/bankr-signals/SKILL.md`
- `skills/bankr-signals/HEARTBEAT.md`
- `skills/bankr-signals/references/api-reference.md`
- `skills/bankr-signals/scripts/publish-signal.sh`
- `skills/shared-agent-skill-foundation/SKILL.md`
- `skills/shared-agent-skill-foundation/references/description-rules.md`
- `skills/dashboard-development/SKILL.md`
- `skills/dashboard-development/references/reading-order.md`
- `skills/backend-development/SKILL.md`
- `skills/backend-development/references/reading-order.md`
- `skills/extensions-development/SKILL.md`
- `skills/extensions-development/references/surface-map.md`
- `skills/apps-development/SKILL.md`
- `skills/apps-development/references/operations-map.md`
- `/Users/fahmifareed/.codex/skills/superpowers/writing-skills/SKILL.md`
