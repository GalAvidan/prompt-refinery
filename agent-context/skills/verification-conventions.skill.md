# Skill: Verification Conventions

## id

verification-conventions

## applies_to

Checking Prompt Refinery changes before commit or PR creation.

## Purpose

Capture the lightweight checks that fit this Markdown-only skill repository.

## When to Use

- Adding or updating ALES files.
- Updating root agent entrypoints.
- Preparing a PR for Prompt Refinery documentation or reference changes.

## Steps

1. Validate JSON files under `agent-context/` with a JSON parser.
2. Check that required ALES files exist: `ales.manifest.json`, `map/modules.json`, `map/apis.json`, `map/_provenance.json`, `tasks/refresh-map.task.md`, and `tasks/check-staleness.task.md`.
3. Check that no uppercase agent entrypoint such as `AGENT.md` or `AGENTS.md` exists.
4. Confirm `reference/techniques/` still contains numbered files matching the ten categories in `reference/taxonomy.md`.
5. Review `index.md` and `agent.md` against `SKILL.md` so navigation guidance does not contradict the official procedure.

## Constraints

- Do not treat Markdown reference content as generated output during routine checks.
- Do not commit unrelated workspace changes.

## Verification

- The working tree shows only intentional Prompt Refinery files before commit.
- The PR summary includes validation results and explicitly notes the lowercase filename rule.

## Ask When

- Validation requires changing reference content semantics rather than fixing generated ALES context.