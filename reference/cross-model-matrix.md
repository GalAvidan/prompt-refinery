# Cross-Model Comparison Matrix

Quick-lookup table for the prompt-refining procedure. Find the target model → see which techniques to add/remove/adjust.

## Universal Patterns (Apply to ALL models)

1. Be specific and explicit
2. Define completion criteria
3. Use structured delimiters (XML/markdown)
4. Remove legacy over-specification
5. Provide intent/context (why you're asking)
6. Don't default to max effort/reasoning
7. Self-verify on long runs
8. Enable autonomy with clear boundaries

## Key Parameters by Model

| Model | Effort/Reasoning | Verbosity Control | Thinking | Temperature | Subagents |
|-------|-----------------|-------------------|----------|-------------|-----------|
| Claude Fable 5 | effort (default: high) | Prompt only | Always on (hidden) | Supported | Very ready |
| Claude Sonnet 5 | effort (default: high) | Prompt only | On by default (toggleable) | ❌ 400 error | Moderate |
| Claude Opus 4.8 | effort (start: xhigh) | Prompt only | Off (opt-in) | Supported | Fewer (steerable) |
| Claude general (older) | effort | Prompt only | Varies | Supported | Varies |
| GPT-5.5 | reasoning_effort (start low) | verbosity param | Built-in | N/A | Parallel tools |
| GPT-5.4 | reasoning_effort | verbosity param | Built-in | N/A | Parallel tools |
| GPT-5.3 Codex | reasoning_effort (med default) | N/A | Built-in | N/A | Parallel tools |
| GPT-5.2 | reasoning_effort | N/A | Built-in | N/A | Parallel tools |
| GPT-5.1 | reasoning_effort + `none` mode | verbosity param | Built-in | N/A | Parallel tools |
| GPT-5 | reasoning_effort (med default) | verbosity param | Built-in | N/A | Parallel tools |
| GPT-4.1 | N/A (not reasoning) | N/A | N/A (prompt CoT) | Supported | Parallel tools |
| Gemini (all) | None | Prompt only | Built-in | Supported | N/A |
| Kimi (all) | None | Prompt only | N/A | Supported | N/A |

## Critical Do/Don't by Model

| Model | DO | DON'T |
|-------|-----|-------|
| Claude Fable 5 | Set boundaries; use send-to-user tool; provide memory file | Ask to reproduce reasoning; show context budget; over-specify |
| Claude Sonnet 5 | Remove temperature params; state scope explicitly | Rely on old forced-status scaffolding; expect inference of unstated scope |
| Claude Opus 4.8 | Start at xhigh effort; encourage tool use; guide subagent spawning | Default to max (diminishing returns); expect eager tool use |
| Claude (older) | Use XML tags; give role; 3-5 examples; put long docs at top | Use prefilled responses on 4.6+ (400 error) |
| GPT-5.5 | Write outcome-first prompts; define personality+collaboration; use preambles | Carry over legacy process-heavy prompts; default to high effort |
| GPT-5.4 | Define output contracts (XML); set follow-through policy; verify phase field | Assume higher effort is always better |
| GPT-5.3 Codex | Remove ALL preambles/plans; bias to action; use apply_patch | Prompt for status updates (causes early stopping); use shell over tools |
| GPT-5.2 | Give concrete length constraints; prevent scope drift; re-ground in long context | Let model add extra features; use narrative paragraphs for instructions |
| GPT-5.1 | Define personality persona; use verbosity+reasoning independently | Mix conflicting instructions; expect completeness without prompting for it |
| GPT-5 | Use Responses API; check for contradictions; control eagerness; use metaprompting | Include contradictory instructions; use old "maximize context" prompts |
| GPT-4.1 | Use tools API field; add 3 reminders (persist+tools+plan); prompt for CoT | Manually inject tool schemas; rely on model to infer intent |
| Gemini | Use few-shot examples (primary mechanism); use completion strategy; add constraints | Expect model-specific behavior; rely on reasoning parameters |
| Kimi | Assign role; use delimiters; define steps explicitly; provide reference text | Expect agentic behavior; rely on complex multi-turn patterns |
