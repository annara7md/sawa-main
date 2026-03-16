# Agent Skills Script Usage Analysis

- scope: shared
- purpose: Capture the current guidance for when scripts belong in skills and how those scripts should behave.
- read_when: Read before adding a `scripts/` directory to any local skill.
- source_paths: `https://agentskills.io/skill-creation/using-scripts`
- last_reviewed: 2026-03-14

## Summary

The current scripts guide distinguishes between one-off commands referenced directly from `SKILL.md` and reusable bundled scripts stored in `scripts/`. It explicitly recommends using scripts when repeated helper work is stable and worth packaging.

The guide also states that scripts for agentic use must avoid interactive behavior and should expose a clear interface.

## Key Rules

- Avoid interactive prompts; agent execution is non-interactive.
- Accept inputs through flags, environment variables, or stdin.
- Provide concise `--help` output.
- Use helpful error messages.
- Prefer structured outputs when possible.
- Use meaningful exit codes and safe defaults.

## Implications for Sawa Main

- The initial skills program does not need scripts unless repeated helper work appears during real execution.
- If scripts are later introduced, they should follow the same non-interactive discipline already favored by local automation practices.
- Skill-local script guidance should be derived from this file rather than inventing local script conventions.

## Source URLs

- `https://agentskills.io/skill-creation/using-scripts`
