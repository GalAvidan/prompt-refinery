# Code Generation & Editing

Producing, reviewing, and modifying code reliably.

## When to Apply
- Prompt types: agentic, structured-output
- Coding assistants and autonomous coding agents
- Code review systems
- When code output is over-engineered or under-tested

## Model-Specific Patterns

### Anthropic (Claude)
- Anti-over-engineering: "Only make changes directly requested or clearly necessary. Don't add features, refactor code, or make improvements beyond what was asked."
- Opus 4.8: Strong design instincts. Specify concrete palette/fonts/layout OR ask it to propose options.
- Sonnet 5: For code review: "Report every issue including low-severity. Your goal is coverage."
- Fable 5: First-shot correctness on well-specified problems. Brief specs > detailed instructions.
- File hygiene: "If you create temporary files for iteration, clean them up at the end."

### OpenAI (GPT)
- GPT-5.3 Codex: Use `apply_patch` for diffs. Remove ALL preambles (causes early stopping). "Bias to action; implement with reasonable assumptions."
- GPT-5: Self-reflection rubric: "Create rubric with 5-7 categories. Iterate until top marks."
- GPT-5.4: Output contracts for structured code output. Evidence-grounded reviews.
- GPT-4.1: Prompt explicitly for planning: "Plan extensively before each function call."
- All GPT: Prefer dedicated tools over shell commands for code operations.

### Google (Gemini)
- Structured output API for JSON/schema generation (not prompts)
- Completion strategy: provide the start of code format → model continues
- Few-shot examples for code style/pattern matching

### Moonshot (Kimi)
- Not specifically documented for code generation
- Step-by-step decomposition for complex code tasks
- Reference text pattern for code review (provide code as reference)

## Universal Guidance
- Specify what "done" looks like: tests pass, types check, lints clean
- For reviews: separate finding issues (step 1) from filtering/ranking (step 2)
- Prevent over-engineering: "Don't add error handling for scenarios that can't happen"
- Prevent test-gaming: "Implement actual logic that works for all valid inputs, not just test cases"

## Common Mistakes
- On Opus 4.5/4.6: not constraining scope → creates extra utility files and abstractions
- On GPT-5.3 Codex: adding plan/preamble instructions → causes early stopping
- On Opus 4.8: saying "be conservative" in code review → model follows too faithfully, misses issues
- Not defining code quality criteria → model uses its own (often over-engineered) standards
