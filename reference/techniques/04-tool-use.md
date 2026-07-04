# Tool Use Patterns

When and how models should use tools vs. reason internally.

## When to Apply
- Prompt types: agentic, system-prompt, skill-instruction
- When tool usage rate is too low or too high
- When building tool-using agents or coding assistants

## Model-Specific Patterns

### Anthropic (Claude)
- Sonnet 5: Tool-eager (reaches for tools readily). May overtrigger on 4.6+ — dial back aggressive language.
- Opus 4.8: Favors reasoning over tools. Add: "Use tools when not sure; don't reason from incomplete data."
- Fable 5: Strong parallel tool dispatch. Use `send-to-user` tool for progress updates.
- Higher effort → substantially more tool usage. Raise effort before adding tool prompts.
- Action vs. suggestion: use `<default_to_action>` or `<do_not_act_before_instructions>` blocks.

### OpenAI (GPT)
- GPT-4.1: Use `tools` API field exclusively (2% gain vs manual injection). Name tools clearly. Put examples in `# Examples` section, not tool description.
- GPT-5+: Parallel tool calls native. Define preamble pattern: "Rephrase goal, outline plan, narrate steps."
- GPT-5.3 Codex: Prefer dedicated tools over shell commands. Parallelize independent calls.
- All GPT: Never manually inject tool schemas into system prompt.

### Google (Gemini)
- Use Gemini API's structured output feature for complex JSON schemas (not prompts)
- No native tool-calling framework like Claude/GPT — use function calling API
- Few-shot examples are more effective than descriptions for tool usage patterns

### Moonshot (Kimi)
- Reference text pattern: "Answer using the provided article. If not found, say so."
- No agentic tool calling — treat tools as reference material provided in context
- Use delimiters to separate tool output from instructions

## Universal Guidance
- Be explicit about action vs. suggestion: "Implement changes" vs. "Suggest improvements"
- Name tools clearly with detailed descriptions — this is the primary steering mechanism
- For parallel-safe tools: explicitly encourage parallel execution for speed
- Don't over-prompt tool use on modern models — aggressive language causes overtriggering

## Common Mistakes
- On GPT-4.1: manually injecting tool schemas (2% worse than API field)
- On Opus 4.8: expecting eager tool use without explicit encouragement
- Using "CRITICAL: You MUST use this tool" language on 4.6+ models → overtriggering
- Not raising effort as a first step when tool usage is too low
