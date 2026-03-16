# Agent Skills Best Practices Analysis

- scope: shared
- purpose: Preserve the current authoring principles from Agent Skills best-practices guidance.
- read_when: Read before authoring new skills or deciding what belongs in a skill versus a reference file.
- source_paths: `https://agentskills.io/skill-creation/best-practices`
- last_reviewed: 2026-03-14

## Summary

The current best-practices guide emphasizes that effective skills are grounded in real expertise rather than generic LLM knowledge. It explicitly recommends extracting from real tasks, synthesizing from existing project artifacts, and refining with real execution.

The same guide also emphasizes:

- designing coherent units
- aiming for moderate detail
- structuring larger skills with progressive disclosure
- favoring procedures, checklists, validation loops, and reusable scripts when appropriate

## Key Rules

- Start from real expertise and project-specific material.
- Use execution traces and real task iteration to refine skills.
- Keep `SKILL.md` focused; move detailed material into `references/` when needed.
- Prefer concrete procedures and validation loops over abstract declarations.
- Bundle scripts when the same helper logic is repeatedly reinvented during execution.

## Implications for Sawa Main

- The current workspace should use `memory/`, `AGENTS.md`, existing local skills, and actual source trees as primary inputs.
- The new skills program should not restate generic frontend/backend advice unless it is tied to actual local conventions.
- `memory/agent-skills/` plus skill-local `references/` map well onto the guide’s call for project-specific source material plus progressive disclosure.

## Source URLs

- `https://agentskills.io/skill-creation/best-practices`
