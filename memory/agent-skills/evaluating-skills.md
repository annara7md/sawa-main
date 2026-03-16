# Agent Skills Evaluation Analysis

- scope: shared
- purpose: Capture the current evaluation workflow described for measuring skill output quality.
- read_when: Read before deciding how to validate the new local skills program or iterating on any authored skill.
- source_paths: `https://agentskills.io/skill-creation/evaluating-skills`
- last_reviewed: 2026-03-14

## Summary

The current evaluation guide frames skill quality as an eval-driven loop rather than one-off spot checking. It recommends storing realistic prompts, expected outputs, and optional files in `evals/evals.json`, then comparing runs with the skill against runs without the skill or against a previous version.

The guide describes evaluation components such as:

- clean-context runs
- timing capture
- explicit assertions
- grading with evidence
- aggregate benchmarks
- human review
- iteration based on failed assertions, human feedback, and execution transcripts

## Key Rules

- Compare with-skill runs against a baseline.
- Use realistic prompts and optional input files.
- Keep assertions concrete and verifiable.
- Grade with explicit evidence, not vague approval.
- Review benchmark patterns and human feedback before revising the skill.

## Implications for Sawa Main

- The local skills program should be authored with later evaluation in mind, even if full evals are not built in this turn.
- Domain skills should stay narrow enough that future eval prompts can isolate their value.
- Shared references should make it easier to update a skill from evidence rather than from informal memory.

## Source URLs

- `https://agentskills.io/skill-creation/evaluating-skills`
