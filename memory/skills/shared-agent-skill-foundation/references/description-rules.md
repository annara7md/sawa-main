# Description Rules

## Trigger Principles

- Write `description` as a trigger for when the skill should be loaded.
- Focus on user intent, task shape, and local scope boundaries.
- Keep the scope narrow enough to avoid over-triggering on neighboring skills.
- Keep workflow steps out of `description`; put them in `SKILL.md` or supporting files.

## Good Patterns

- `Use when work is centered on ...`
- `Use when the task is clearly about ...`
- `Use when authoring, reviewing, or maintaining ...`

## Bad Patterns

- describing the internal workflow instead of the trigger
- claiming unsupported capabilities
- using wording so broad that multiple nearby skills would match equally

## Derived From

- `memory/agent-skills/optimizing-descriptions.md`
- `memory/agent-skills/best-practices.md`
