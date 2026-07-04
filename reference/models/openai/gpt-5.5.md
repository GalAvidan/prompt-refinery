# GPT-5.5

Last-verified: 2026-07-04
Source: src-004-openai-gpt-5.5

## Defaults
- Reasoning effort: Start at low/medium before escalating
- Verbosity: API parameter available
- Style: Efficient, direct, task-oriented

## Strengths
- Outcome-first prompts work best (shorter is better)
- More efficient reasoning (low/medium often sufficient)
- Strong personality steering

## Key Prompts to ADD
- Personality block: Define both personality (how it sounds) AND collaboration style (how it works)
- Preamble: "Before tool calls, send short user-visible update (1-2 sentences)"
- Retrieval budget: Define search depth and early-stop criteria
- Outcome-first: Describe what good looks like, constraints, evidence, desired output

## Key Prompts to REMOVE
- Legacy process-heavy prompt stacks from older models
- Over-specified step-by-step instructions (narrows search space)

## Anti-Patterns
- Carrying forward every instruction from older prompts → adds noise
- Defaulting to high reasoning effort → often unnecessary
- Not defining personality for customer-facing agents
