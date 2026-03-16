# Script Guidelines

## When Scripts Belong

- when the same helper logic is repeatedly reinvented across real executions
- when a mechanical check is more reliable as code than as natural-language reasoning

## Required Script Behavior

- non-interactive only
- accept input through flags, environment variables, or stdin
- provide `--help`
- emit useful error messages
- use meaningful exit codes
- prefer structured output when practical

## Local Rule

Do not add `scripts/` to a root skill unless analysis or repeated execution demonstrates a concrete need.

## Derived From

- `memory/agent-skills/using-scripts.md`
- `memory/agent-skills/best-practices.md`
