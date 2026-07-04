# Self-Verification & Grounding

Ensuring correctness, preventing hallucination, and anchoring claims in evidence.

## When to Apply
- All prompt types, especially: structured-output, agentic
- Tasks requiring factual accuracy or source attribution
- Code generation where correctness must be validated
- Research synthesis combining multiple sources

## Model-Specific Patterns

### Anthropic (Claude)
- "Audit each claim against a tool result from this session." — Use verifier subagents for critical output.
- Fable 5: "Progress grounding: audit claims against tool results." Strong first-shot correctness.
- Opus 4.8: Higher recall AND precision in bug-finding. Use two-step review (find → filter).
- Anti-hallucination: "Never speculate about code you haven't opened. Read files before claiming."
- Quote grounding: "Find relevant quotes first, place in `<quotes>` tags, then answer."

### OpenAI (GPT)
- GPT-5: Self-reflection: "Create rubric with 5-7 categories. Iterate until top marks."
- GPT-5.4: Evidence-rich synthesis. Explicit verification checks before irreversible actions.
- GPT-5.3 Codex: Test frequently. "Optimize for correctness, clarity, reliability."
- GPT-4.1: "Plan extensively before each function call, reflect on outcomes after."
- Pattern: Generate → Review against criteria → Refine if needed (self-correction chain)

### Google (Gemini)
- Ground responses in provided documents
- Completion strategy prevents hallucination (model continues provided format)
- For factual tasks: always provide reference material in context

### Moonshot (Kimi)
- "Answer using the provided article. If the answer is not found, write 'I can't find the answer.'"
- Reference text grounding is primary accuracy mechanism
- Provide source material explicitly — model is honest about gaps

## Universal Guidance
- Prevent hallucination: require the model to READ before CLAIMING
- For code: "Investigate files before answering questions about the codebase"
- For research: track confidence levels; identify single-source vs. multi-source claims
- For generation: use generate → review → refine chains for quality-critical output
- Prevent test-gaming: "Implement principled solutions, not workarounds for specific test cases"

## Common Mistakes
- Asking Claude to reproduce its reasoning (triggers refusal on Fable 5)
- Not providing reference material to Kimi/Gemini (they need grounding documents)
- Assuming code claims are correct without file verification
- On GPT: not prompting for self-reflection (model won't self-correct by default)
- Hard-coding values from test cases instead of implementing general solutions
