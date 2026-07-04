# Communication Style & Personality

Tone, warmth, readability, and user-facing interaction patterns.

## When to Apply
- Prompt types: system-prompt, creative, one-liner
- Customer-facing agents requiring consistent voice
- When migrating between models with different tone defaults
- When output tone doesn't match product requirements

## Model-Specific Patterns

### Anthropic (Claude)
- Role in system prompt: even one sentence measurably improves output quality
- Opus 4.8: Direct, opinionated style. Minimal validation-forward phrasing, sparing emoji.
- Fable 5: "Lead with the outcome. First sentence answers 'what happened.'"
- Sonnet 5: Anti-generic aesthetic: "NEVER use generic AI aesthetics (Inter, Roboto, purple gradients)"
- To add warmth: "Use a warm, collaborative tone. Acknowledge the user's framing before answering."
- Positive examples > negative instructions for style control.

### OpenAI (GPT)
- GPT-5.5/5.1: Define BOTH personality (how it sounds) AND collaboration style (how it works)
- GPT-5.5: Use preambles: "Before tool calls, send short user-visible update (1-2 sentences)"
- GPT-5: Personality block persists across turns. Re-instruct if conversation is long.
- Pattern: Personality section + Collaboration section in system prompt

### Google (Gemini)
- System instructions set global tone at conversation level
- Few-shot examples for style (primary mechanism — more effective than description)
- Natural language style matching: prompt tone influences response tone

### Moonshot (Kimi)
- Role assignment via system message (detailed persona with domain + audience)
- Effective with specific role definitions including constraints and audience

## Universal Guidance
- Always assign a role — even generic roles improve output over bare prompts
- Specificity scales: generic < domain < domain+audience < domain+persona+format
- Use examples of desired tone rather than describing it (showing > telling)
- State style scope explicitly on literal models: "Apply this tone to every response"

## Common Mistakes
- Not defining personality for customer-facing GPT agents
- Using "You are a helpful assistant" (essentially the default — adds nothing)
- On Opus 4.8: not specifying concrete alternatives when adjusting aesthetic/style
- Relying on description alone for Gemini (must use few-shot examples)
