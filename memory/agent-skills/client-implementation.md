# Agent Skills Client Implementation Analysis

- scope: shared
- purpose: Preserve the current client-side integration model so the local skills program stays compatible with real Agent Skills lifecycles.
- read_when: Read when deciding how local skills should support discovery, activation, and progressive disclosure across clients.
- source_paths: `https://agentskills.io/client-implementation/adding-skills-support`
- last_reviewed: 2026-03-14

## Summary

The current client implementation guide describes a lifecycle of discovery, parsing, catalog disclosure, activation, and context management. It treats progressive disclosure as the core principle and explains that tier-1 catalog loading should include only minimal metadata such as `name` and `description`.

The guide also discusses:

- filesystem scanning for local skills
- lenient parsing with diagnostics
- building a skill catalog
- model-driven activation versus user-explicit activation
- structured wrapping for activated content
- protecting skill content from context compaction
- deduplicating repeated activations

## Key Rules

- Discovery should be lightweight and rely on `name` plus `description`.
- Activation should load full instructions only when relevant.
- Relative paths inside skill bodies should resolve against the skill directory.
- Clients may use file-read activation or a dedicated activation tool.
- Skill content should be protected from accidental context loss once activated.

## Implications for Sawa Main

- Local skills should keep top-level metadata compact and purposeful because it may be the only thing visible at discovery time.
- Skill-local `references/` and any later `scripts/` should use relative paths that resolve cleanly from each skill directory.
- The local program should assume future portability across clients, not only the current Codex session.

## Source URLs

- `https://agentskills.io/client-implementation/adding-skills-support`
