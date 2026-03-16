# Agent Skills Repository Analysis

- scope: shared
- purpose: Record what is directly visible in the current `agentskills/agentskills` repository structure.
- read_when: Read when aligning the local program with the official repository layout and maintained artifacts.
- source_paths: `https://github.com/agentskills/agentskills`, `https://raw.githubusercontent.com/agentskills/agentskills/main/README.md`
- last_reviewed: 2026-03-14

## Summary

Current repository evidence confirms that the upstream repository contains:

- `.claude/`
- `docs/`
- `skills-ref/`
- top-level files such as `README.md`, `CONTRIBUTING.md`, and `package.json`

The current `docs/` tree includes:

- `docs/home.mdx`
- `docs/what-are-skills.mdx`
- `docs/specification.mdx`
- `docs/skill-creation/`
- `docs/client-implementation/`

The current `skills-ref/` tree is present as a separate package-like area with:

- `skills-ref/src`
- `skills-ref/tests`
- `skills-ref/pyproject.toml`

The current upstream `README.md` describes the repository as containing the specification, documentation, and reference SDK, and links to the docs and example skills.

## Key Rules

- The official repository separates docs and reference implementation concerns.
- The upstream structure confirms that docs, examples or references, and implementation support can live in distinct top-level areas.
- The upstream README points to examples outside the main repo, so example-skill material should not be assumed to live directly in this repository.

## Implications for Sawa Main

- Keeping `memory/` separate from `skills/` is consistent with the upstream split between documentation and reference implementation layers.
- Keeping support files colocated inside skill packages is still compatible with that split, because the separation that matters is between memory/documentation and executable skill packages.
- The local program should not assume example skill packs exist inside the upstream repo if the current repo does not expose them there.
- A root `skills/` directory in `sawa-main/` remains compatible with the upstream model while still being project-specific.

## Source URLs

- `https://github.com/agentskills/agentskills`
- `https://raw.githubusercontent.com/agentskills/agentskills/main/README.md`
