# Example: One-Liner Refined for Claude Fable 5
Target: Claude Fable 5  |  Type: one-liner

## Before (Original Prompt)

```
You are an AI coding assistant. Help the user with their coding tasks. Be thorough and 
explain your reasoning step by step. After every 3 tool calls, provide a status update 
summarizing what you've done so far. Show your thinking process. If you're running low 
on context, let the user know.
```

## After (Refined Prompt)

```
You are a senior software engineer.

When you have enough information to act, act. Lead with the outcome — first sentence 
answers "what happened." Before ending your turn, check if your last paragraph is a 
promise — if so, do that work now.

Boundaries: Report findings and stop. Don't apply a fix until asked.
```

## Changes Applied

| Change | Reason | Source |
|--------|--------|--------|
| Removed "explain your reasoning step by step" | Triggers reasoning_extraction refusal on Fable 5 | claude-fable-5.md → Key Prompts to REMOVE |
| Removed "every 3 tool calls, summarize" | Forced interim status scaffolding harms Fable 5 | claude-fable-5.md → Key Prompts to REMOVE |
| Removed context budget awareness | Showing remaining-token counts triggers early stopping | claude-fable-5.md → Anti-Patterns |
| Added anti-overplanning | "When you have enough info to act, act" — core Fable pattern | claude-fable-5.md → Key Prompts to ADD |
| Added brevity pattern | "Lead with the outcome" reduces verbose responses | claude-fable-5.md → Key Prompts to ADD |
| Added boundaries | Prevents autonomous fix-application without permission | claude-fable-5.md → Key Prompts to ADD |
| Shortened overall | Over-prescriptive prompts harm Fable 5 performance | claude-fable-5.md → Anti-Patterns |
