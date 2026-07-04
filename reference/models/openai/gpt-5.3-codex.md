# GPT-5.3 Codex

Last-verified: 2026-07-04
Source: src-006-openai-gpt-5.3-codex

## Defaults
- Reasoning effort: medium (interactive); high/xhigh (hardest tasks)
- Compaction: First-class support for multi-hour sessions
- Style: Autonomous senior engineer

## Strengths
- Token-efficient agentic coding
- Long-running autonomy (hours)
- PowerShell/Windows environments
- Uninterrupted code execution

## Key Prompts to ADD
- Autonomy: "Proactively gather context, plan, implement, test, refine without waiting."
- Persistence: "Persist until task is fully handled end-to-end within current turn."
- Bias to action: "Default to implementing with reasonable assumptions."
- Tool preference: "Use rg over grep; dedicated tools over shell; parallelize independent calls."
- Code quality: "Optimize for correctness, clarity, reliability. Follow codebase conventions."

## Key Prompts to REMOVE
- ❌ ALL preambles, plans, or status updates during rollout (causes early stopping)
- ❌ "Communicate an upfront plan" instructions
- ❌ Old "maximize context understanding" prompts

## Anti-Patterns
- Prompting for preambles/plans → model stops abruptly before completion
- Using shell commands when dedicated tools exist
- Non-ASCII characters without justification
- Reverting existing changes not made by the model
