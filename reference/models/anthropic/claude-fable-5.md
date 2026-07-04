# Claude Fable 5

Last-verified: 2026-07-04
Source: src-001-anthropic-fable-5

## Defaults
- Effort: high (use xhigh for capability-sensitive)
- Thinking: Always on, not toggleable
- Temperature: Supported
- Turns: Can run for hours autonomously

## Strengths
- Long-horizon autonomy (multi-day runs)
- First-shot correctness on well-specified problems
- Parallel subagent dispatch
- Strong instruction following from brief instructions

## Key Prompts to ADD
- Boundaries: "Report findings and stop. Don't apply a fix until asked."
- Anti-overplanning: "When you have enough information to act, act."
- Brevity: "Lead with the outcome. First sentence answers 'what happened.'"
- Progress grounding: "Audit each claim against a tool result from this session."
- Memory: "Store one lesson per file with a one-line summary at the top."
- Autonomy: "Before ending your turn, check if last paragraph is a promise—if so, do that work now."

## Key Prompts to REMOVE
- "Show your reasoning" / "explain your thinking" (triggers reasoning_extraction refusal)
- Forced interim status scaffolding ("every 3 tool calls, summarize")
- Over-prescriptive skills from prior models
- Context budget countdowns (triggers early stopping)

## Anti-Patterns
- Asking to reproduce reasoning in response → refusal
- Showing remaining-token counts → premature session ending
- Over-engineering prompts → model does it better with less instruction
