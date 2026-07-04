# Subagents & Delegation

Parallel execution and task decomposition across multiple agents.

## When to Apply
- Prompt types: agentic, skill-instruction
- Multi-file operations, fan-out workloads, independent parallel tasks
- When spawning behavior is too aggressive or too conservative

## Model-Specific Patterns

### Anthropic (Claude)
- Fable 5: Very ready for subagents. Dispatches readily and proactively. Set boundaries to prevent over-delegation.
- Opus 4.8: Spawns FEWER subagents by default. Steer with: "Spawn multiple subagents when fanning out across items or reading multiple files."
- Opus 4.6: Over-spawns subagents. Add: "Work directly rather than delegating for simple tasks."
- Guidance to balance: "Use subagents when tasks can run in parallel or require isolated context. For single-file edits or sequential operations, work directly."

### OpenAI (GPT)
- All GPT models: Parallel tool calls (not subagents per se, but equivalent fan-out)
- GPT-5: Responses API enables reasoning persistence across turns
- GPT-5.3 Codex: Parallelize independent tool calls. Use dedicated tools over shell.
- Pattern: Break large tasks across turns; use parallel calls within each turn

### Google (Gemini)
- No subagent framework documented
- For parallel work: use multiple API calls orchestrated externally
- Not applicable at the prompt level

### Moonshot (Kimi)
- No subagent capability
- For complex tasks: break down explicitly; chunk long documents recursively
- Use "summary of summaries" pattern for large document processing

## Universal Guidance
- Subagents are appropriate for: parallel-independent tasks, isolated contexts, fan-out
- Work directly for: simple tasks, sequential operations, shared-state work
- Always specify WHEN to delegate vs. when to work directly
- Monitor for overuse (spawning for single-file edits) and underuse (serial fan-out)

## Common Mistakes
- On Opus 4.8: not prompting for subagent use (defaults to fewer than needed)
- On Opus 4.6: not constraining subagent use (defaults to too many)
- Expecting subagent behavior from Gemini or Kimi (not supported)
- Spawning subagents for sequential tasks where ordering matters
