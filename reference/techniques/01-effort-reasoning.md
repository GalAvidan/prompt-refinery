# Effort & Reasoning Control

Calibrating the model's thinking depth vs. cost/latency tradeoff.

## When to Apply
- All prompt types, especially: agentic, system-prompt
- When response quality is insufficient or costs are too high
- When tool use rate is lower than expected (raise effort first)

## Model-Specific Patterns

### Anthropic (Claude)
- **Parameter:** `effort` (low → medium → high → xhigh → max)
- Fable 5: Default `high`; use `xhigh` for capability-sensitive. Thinking always on (hidden).
- Sonnet 5: Default `high`; `medium` ≈ old Sonnet 4.6 at `high`. Adaptive thinking ON by default.
- Opus 4.8: Start at `xhigh` (most impactful ever). Thinking OFF unless `thinking: {type: "adaptive"}`.
- Higher effort → substantially more tool usage. Raise effort before adding aggressive prompts.
- To reduce overthinking: lower effort OR add `"When in doubt, respond directly."`

### OpenAI (GPT)
- **Parameter:** `reasoning_effort` (none → low → medium → high → xhigh)
- GPT-5.5: Start low/medium; escalate only if quality demands it
- GPT-5.3 Codex: medium default; high/xhigh only for hardest tasks
- GPT-5/5.4: Task-dependent; higher is NOT always better
- GPT-4.1: No reasoning parameter (not a reasoning model) — prompt for CoT explicitly

### Google (Gemini)
- No effort/reasoning parameter — uniform behavior regardless of task difficulty
- Cannot calibrate thinking depth via API; rely on prompt complexity to drive depth

### Moonshot (Kimi)
- No effort/reasoning parameter
- Rely on step-by-step decomposition in the prompt to encourage deeper reasoning

## Universal Guidance
- Start at medium effort; escalate only when quality requires it
- Defaulting to max is wasteful — diminishing returns and overthinking are common
- If responses are shallow: raise effort BEFORE adding verbose prompting
- If responses overthink: lower effort OR add constraint prompts

## Common Mistakes
- Defaulting to max effort on every task (wastes tokens, can cause overthinking)
- Adding "think harder" prompts instead of raising the effort parameter
- On GPT-4.1: forgetting it needs explicit CoT prompting (no built-in reasoning)
- On Claude Opus 4.8: forgetting thinking is OFF by default (must opt in)
