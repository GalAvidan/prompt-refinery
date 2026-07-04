# Gemini (All Models)

Last-verified: 2026-07-04
Source: src-012-google-gemini-prompting
Covers: Gemini 2.5 Pro, 3.1 Pro, 3.5 Flash, and all other Gemini variants

## Defaults
- No effort/reasoning parameter (uniform behavior)
- Temperature: Supported (standard sampling)
- No adaptive thinking toggle
- System instructions available

## Strengths
- Few-shot examples as primary steering mechanism
- Completion strategy (provide format start → model continues)
- Structured output API for complex JSON schemas
- Iterative prompt engineering approach

## Key Prompts to ADD
- Few-shot examples: ALWAYS include (prompts without them are "likely less effective")
- Constraints: State format/length explicitly ("Summarize in one sentence")
- Completion strategy: Provide the START of your desired output format
- System instruction: Set global tone/style at conversation level
- Response format: Request explicitly (table, bullets, keywords, etc.)

## Key Prompts to REMOVE
- XML tag conventions (not native to Gemini; use natural language instead)
- Effort/reasoning parameters (don't exist)
- Adaptive thinking toggles (don't exist)
- Complex agentic persistence prompts (not documented for Gemini)

## Anti-Patterns
- Relying on zero-shot for format control → use few-shot examples instead
- Too many examples → overfitting risk
- Not specifying constraints → model chooses its own format
- Using prompts designed for Claude/GPT agentic patterns

## Key Differences from Claude/GPT
- No XML tag convention — natural language formatting preferred
- No effort dial — model behavior is uniform regardless of task difficulty
- Few-shot examples are MORE important than in Claude/GPT (primary steering)
- Completion strategy replaces many explicit format instructions
- For complex JSON: use Gemini API's structured output feature, not prompts
