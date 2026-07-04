# Prompt Refinery Index

Prompt Refinery is a Markdown agent skill for refining prompts against model-specific guidance.

## Load Order

1. `SKILL.md` - official trigger phrases, workflow, and execution procedure.
2. `agent.md` - operating contract for agents using this skill.
3. `reference/taxonomy.md` - technique categories used to classify the prompt.
4. `reference/models/<vendor>/<model>.md` - target model guidance when documented.
5. `reference/cross-model-matrix.md` - quick comparison for model-specific differences.
6. `reference/techniques/` - technique deep dives selected by prompt type.
7. `examples/` - before and after examples for similar prompt shapes.

## Navigation

- `README.md` - short human overview and usage note.
- `SKILL.md` - authoritative skill procedure.
- `agent.md` - agent behavior boundaries and fallback rules.
- `reference/universal.md` - fallback guidance for undocumented models.
- `reference/models/anthropic/` - Anthropic model guidance.
- `reference/models/google/` - Google model guidance.
- `reference/models/moonshot/` - Moonshot model guidance.
- `reference/models/openai/` - OpenAI model guidance.
- `reference/techniques/` - ten numbered technique categories.
- `examples/` - six numbered demonstrations.
- `agent-context/` - ALES v2 context for map, task, and project-specific skill discovery.

## Agent Notes

- Treat `SKILL.md` as the source of truth for the refinement workflow.
- Treat files under `reference/` as read-only during prompt refinement.
- Use `agent.md` when deciding how much context to load and when to ask the user for a target model.
- Keep generated agent-facing filenames lowercase. Do not create `AGENT.md` or `AGENTS.md`.