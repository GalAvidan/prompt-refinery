# Skill: Prompt Refinement Workflow

## id

prompt-refinement-workflow

## applies_to

Rewriting prompts through the `SKILL.md` six-step procedure.

## Purpose

Capture the concrete Prompt Refinery workflow for turning an input prompt into a model-specific refined prompt.

## When to Use

- The user asks to optimize, refine, improve, rewrite, or adapt a prompt.
- The user provides a prompt and a target model or target model family.
- The user is building a system prompt, skill instruction, agent workflow, creative prompt, or structured-output prompt.

## Steps

1. Identify the target model exactly as described in `SKILL.md`.
2. Classify the prompt type using the six Prompt Refinery prompt types: `one-liner`, `system-prompt`, `skill-instruction`, `agentic`, `creative`, or `structured-output`.
3. Load model guidance and technique files through `reference-navigation.skill.md`.
4. Rewrite the prompt while preserving the user's original intent.
5. Adjust formatting, verbosity, reasoning guidance, tool-use instructions, and output shape only when the loaded references support the change.
6. Return the refined prompt ready to use, followed by brief notes on what changed and why.
7. Re-read the loaded model reference before final output and remove unsupported or conflicting patterns.

## Constraints

- Do not change what the prompt asks for.
- Do not leave placeholders unless the user requested a reusable template.
- Do not apply a technique only because it is generally popular; it must fit the target model or universal fallback guidance.

## Verification

- The output includes a usable refined prompt.
- The change notes cite the loaded model or universal reference at a high level.
- The self-verification pass confirms no loaded model guidance was contradicted.

## Ask When

- Refining would require inventing missing goals, tools, data sources, or output requirements.