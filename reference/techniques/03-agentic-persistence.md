# Agentic Persistence & Autonomy

Keeping the model working through multi-step tasks without premature stopping.

## When to Apply
- Prompt types: agentic, system-prompt
- Long-running autonomous tasks (coding, research, migrations)
- Tasks expected to exceed a single context window

## Model-Specific Patterns

### Anthropic (Claude)
- Fable 5: Multi-day autonomy. Add boundaries, NOT persistence prompts. Key: "When you have enough info to act, act." Remove context budget countdowns (triggers early stopping).
- Opus 4.8: Strong long-horizon work. Set 64k+ max_tokens at high/xhigh effort.
- Sonnet 5: State scope explicitly — does NOT infer unstated requirements.
- Anti-stopping: "Before ending your turn, check if last paragraph is a promise — if so, do that work now."
- Context compaction: "Do not stop tasks early due to token budget concerns. Save state before refresh."

### OpenAI (GPT)
- GPT-5.3 Codex: "Persist until task is fully handled end-to-end." **REMOVE all preambles/plans** (causes early stopping). Bias to action over communication.
- GPT-5: "Keep going until resolved. Never stop on uncertainty — deduce and continue."
- GPT-4.1: Three-reminder pattern (+20% SWE-bench): persistence + tool-calling + planning.
- Use Responses API with `previous_response_id` for reasoning persistence across turns.

### Google (Gemini)
- No agentic persistence framework documented
- For multi-step tasks: decompose into explicit sequential calls (prompt chaining)

### Moonshot (Kimi)
- Single-turn focused; no multi-turn persistence
- For complex tasks: chunk and process recursively; summarize between rounds

## Universal Guidance
- Define "done" explicitly — completion criteria prevent premature stopping
- Provide autonomy with boundaries (what to do, what NOT to do, when to stop)
- For long tasks: enable state saving ("Save progress to a file before context fills")
- Minimal-solution discipline: prevent over-engineering during autonomous work

## Common Mistakes
- On Fable 5: showing remaining token counts → premature session ending
- On GPT-5.3 Codex: adding preamble/plan instructions → causes early stopping
- Not defining completion criteria → model stops when it "feels done"
- Over-prescribing steps from prior models → narrows the model's solution space
