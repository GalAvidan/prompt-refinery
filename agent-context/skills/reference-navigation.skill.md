# Skill: Reference Navigation

## id

reference-navigation

## applies_to

Prompt Refinery reference loading and context selection.

## Purpose

Capture the project-specific load order for using `reference/` without reading every model and technique file.

## When to Use

- A prompt refinement task names or implies a target model.
- The agent needs to choose which reference files to load before rewriting a prompt.
- The user asks for cross-model adaptation or comparison.

## Steps

1. Start with `SKILL.md` and `agent.md` to confirm the task fits Prompt Refinery.
2. Load `reference/taxonomy.md` to classify the prompt type.
3. Load the target model file under `reference/models/<vendor>/<model>.md` when it exists.
4. Load `reference/universal.md` when the model is undocumented.
5. Load `reference/cross-model-matrix.md` when the task compares models or when a model-specific technique might conflict.
6. Load only the technique files from `reference/techniques/` that match the classified prompt type.

## Constraints

- Files under `reference/` are read-only during normal skill execution.
- Do not load every vendor folder for a single-model refinement.
- Do not invent a model file path when the documented model does not exist.

## Verification

- The final response names whether model-specific or universal guidance was used.
- Every applied model-specific pattern can be traced to the loaded model file or matrix.

## Ask When

- The user does not name a target model and the active context does not imply one.