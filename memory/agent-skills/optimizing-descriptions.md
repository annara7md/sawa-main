# Agent Skills Description Optimization Analysis

- scope: shared
- purpose: Capture the current guidance for writing `description` fields that trigger reliably.
- read_when: Read before drafting or revising the `description` field of any local skill.
- source_paths: `https://agentskills.io/skill-creation/optimizing-descriptions`
- last_reviewed: 2026-03-14

## Summary

The current description guide states that `description` is the primary mechanism used to decide whether a skill should be loaded. It warns that under-specified descriptions miss valid activations and over-broad descriptions trigger unnecessarily.

The guide currently recommends:

- imperative phrasing
- focusing on user intent rather than implementation
- being explicit about contexts where the skill applies
- staying concise and under the 1024-character limit

It also recommends eval-driven description optimization using should-trigger and should-not-trigger queries, including near misses and realistic prompts.

## Key Rules

- Write `description` as an instruction to the agent, not a passive summary.
- Describe the user’s goal, not the internals of the skill.
- Design trigger eval queries that include realistic phrasing and near misses.
- Avoid overfitting description changes to a narrow set of eval prompts.

## Implications for Sawa Main

- Descriptions for `dashboard-development` and `backend-development` should describe when the user is asking for dashboard or backend work, not list internal file structures alone.
- The local skills program should preserve domain boundaries in descriptions so adjacent skills do not false-trigger.
- `extensions-development` and `apps-development` should only claim scopes that local evidence actually supports.

## Source URLs

- `https://agentskills.io/skill-creation/optimizing-descriptions`
