# Prompt Refinery Agent Contract

This file defines how agents should use Prompt Refinery without loading the entire reference tree by default.

## Expected Input

The user should provide a prompt to refine and, ideally, the target model or model family. If the target model is missing and cannot be inferred from the active context, ask which model the prompt will run on.

## Operating Flow

1. Load `SKILL.md` for the official workflow.
2. Identify the target model from the user request, active agent mode, or conversation context.
3. If the model is documented, load the matching file from `reference/models/<vendor>/<model>.md`.
4. If the model is not documented, load `reference/universal.md` and state that universal guidance is being used.
5. Classify the prompt type using `SKILL.md` and `reference/taxonomy.md`.
6. Load only the technique files that match the prompt type, then add secondary technique files only when the prompt clearly spans multiple types.
7. Use `reference/cross-model-matrix.md` to check for model-specific conflicts before finalizing the rewrite.
8. Return the refined prompt and brief change notes.
9. Re-check the loaded model guidance before final output and remove patterns that conflict with it.

## Context Boundaries

- Do not modify files under `reference/` while executing the skill.
- Do not load every model file unless the task is explicitly cross-model analysis.
- Do not change the user's intent while improving structure, clarity, or model fit.
- Do not leave placeholders in the refined prompt unless the user explicitly asks for a template.
- Do not invent model guidance when no model reference exists; use `reference/universal.md` instead.

## Ask When

- The target model cannot be inferred.
- The user asks for optimization across incompatible target models and does not name a priority model.
- The source prompt is incomplete enough that refinement would require inventing missing goals, tools, data, or output requirements.

## Filename Rule

Agent-facing files in this project use lowercase names. Do not create `AGENT.md`, `AGENTS.md`, or other all-capital agent entrypoint files.