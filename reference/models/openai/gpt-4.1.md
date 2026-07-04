# GPT-4.1

Last-verified: 2026-07-04
Source: src-010-openai-gpt-4.1

## Defaults
- NOT a reasoning model (no internal chain of thought)
- Temperature: Supported
- Tools: Use `tools` API field exclusively

## Strengths
- Literal, close instruction following
- Strong coding and long-context
- API-native tool use
- Highly steerable with single-sentence corrections

## Key Prompts to ADD (Three Reminders — +20% SWE-bench)
1. Persistence: "You are an agent—keep going until completely resolved."
2. Tool-calling: "If not sure, use tools to read files. Do NOT guess."
3. Planning: "Plan extensively before each function call, reflect on outcomes."

Additional:
- Use tools API field (2% gain vs manual injection)
- Put examples in `# Examples` section, not tool description
- Name tools clearly with detailed descriptions

## Key Prompts to REMOVE
- Manually injected tool schemas in system prompt (use API field)
- Vague instructions expecting model to infer intent

## Anti-Patterns
- Not prompting for CoT → model doesn't plan (it's not a reasoning model)
- Manual tool schema injection → 2% worse than API field
- Expecting reasoning without explicit planning prompt
