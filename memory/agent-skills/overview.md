# Agent Skills Overview

- scope: shared
- purpose: Capture the core purpose and loading model of Agent Skills from the current documentation.
- read_when: Read first before authoring or reviewing any local Agent Skill in this workspace.
- source_paths: `https://agentskills.io/home`, `https://agentskills.io/what-are-skills`
- last_reviewed: 2026-03-14

## Summary

The current Agent Skills docs describe skills as a lightweight, open format for extending AI agent capabilities with specialized knowledge and workflows. A skill is presented as a folder centered on `SKILL.md`, with optional `scripts/`, `references/`, and `assets/`.

The docs define the core loading model as progressive disclosure:

- discovery loads only `name` and `description`
- activation loads the full `SKILL.md`
- execution may load referenced files or bundled scripts as needed

## Key Rules

- A skill is meant to add knowledge or capabilities the agent would not reliably have on its own.
- The folder format is portable and intended to work across multiple agent clients.
- Optional directories exist to support deeper context without forcing everything into `SKILL.md`.

## Implications for Sawa Main

- Local skills should stay scoped enough that `description` can trigger them accurately from user intent.
- The current `memory/` system is a good upstream source for progressive disclosure because it already separates shared, dashboard, and backend knowledge.
- The local skills program should keep common rules out of domain skills when those rules can live in shared references.

## Source URLs

- `https://agentskills.io/home`
- `https://agentskills.io/what-are-skills`
