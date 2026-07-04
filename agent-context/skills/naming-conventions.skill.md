# Skill: Naming Conventions

## id

naming-conventions

## applies_to

Adding or updating files in Prompt Refinery.

## Purpose

Capture the filename and folder conventions already used by this Markdown skill repository.

## When to Use

- Adding examples, reference files, ALES context files, or agent-facing docs.
- Renaming generated files for agent discovery.
- Checking whether a proposed filename fits the repository.

## Steps

1. Use lowercase folder names such as `examples`, `reference`, `models`, and `techniques`.
2. Use lowercase kebab-case for generated agent and ALES files.
3. Number examples with a two-digit prefix, as in `examples/01-one-liner-to-claude-fable.md`.
4. Number technique files with a two-digit taxonomy prefix, as in `reference/techniques/10-self-verification.md`.
5. Keep model vendor folder names lowercase: `anthropic`, `google`, `moonshot`, and `openai`.
6. Use lowercase root agent entrypoints such as `index.md` and `agent.md`.

## Constraints

- Do not create `AGENT.md`, `AGENTS.md`, or other all-capital agent entrypoint files.
- Do not rename existing reference files as part of routine ALES maintenance.
- Do not add unnumbered technique files unless the taxonomy changes first.

## Verification

- New generated filenames are lowercase or lowercase kebab-case.
- New examples and techniques follow the existing numeric prefix pattern when applicable.
- No uppercase agent entrypoint exists in the repository root.

## Ask When

- A requested filename conflicts with the lowercase naming rule.