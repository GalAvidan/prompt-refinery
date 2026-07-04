# GPT-5

Last-verified: 2026-07-04
Source: src-009-openai-gpt-5

## Defaults
- Reasoning effort: medium (scale up/down per task)
- Verbosity: API parameter available
- API: Use Responses API (significant perf gains)

## Strengths
- Most steerable model (extraordinarily receptive to instructions)
- Strong agentic task performance
- Excellent coding and frontend taste
- Metaprompting (use GPT-5 to optimize its own prompts)

## Key Prompts to ADD
- Responses API: Use `previous_response_id` for reasoning persistence
- Eagerness control: Define criteria for exploration depth + stop conditions
- Tool preambles: "Rephrase user's goal, outline plan, narrate steps, summarize."
- Persistence: "Keep going until resolved. Never stop on uncertainty—deduce and continue."
- Self-reflection: "Create rubric with 5-7 categories. Iterate until top marks."
- XML specs: Use `<instruction_spec>` for improved adherence

## Key Prompts to REMOVE
- Old "maximize context understanding" / "be THOROUGH" prompts (causes over-searching)
- Contradictory instructions (extremely costly—wastes reasoning tokens)
- Markdown assumptions (not default in API; must prompt for it)

## Anti-Patterns
- Contradictory instructions → model wastes tokens trying to reconcile
- Not using Responses API → significant perf loss (73.9% vs 78.2% on benchmarks)
- Markdown instruction degradation over long conversations → re-instruct every 3-5 messages
