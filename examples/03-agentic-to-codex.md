# Example: Agentic Prompt Refined for GPT-5.3 Codex
Target: GPT-5.3 Codex  |  Type: agentic

## Before (Original Prompt)

```
You are an autonomous coding agent. Before starting any task:
1. Communicate an upfront plan of what you intend to do
2. List all files you'll need to modify
3. Provide a status update after each step
4. When complete, summarize all changes made

Use grep to search for code. If you're not sure about something, ask the user.
Maximize your context understanding before making changes.
```

## After (Refined Prompt)

```
You are an autonomous senior engineer.

Proactively gather context, plan, implement, test, and refine without waiting for 
instructions. Persist until the task is fully handled end-to-end within the current turn.
Default to implementing with reasonable assumptions. If the task is ambiguous, bias 
toward the most likely interpretation and proceed.

Use rg over grep. Use dedicated tools over shell commands. Parallelize independent 
tool calls. Optimize for correctness, clarity, and reliability. Follow existing 
codebase conventions.
```

## Changes Applied

| Change | Reason | Source |
|--------|--------|--------|
| Removed "Communicate an upfront plan" | ❌ Causes early stopping on Codex | gpt-5.3-codex.md → Key Prompts to REMOVE |
| Removed all preamble/status instructions | ❌ Status updates cause abrupt stopping | gpt-5.3-codex.md → Key Prompts to REMOVE |
| Removed "maximize context understanding" | Legacy prompt from older models | gpt-5.3-codex.md → Key Prompts to REMOVE |
| Removed "ask the user" | Contradicts autonomous operation | gpt-5.3-codex.md → Key Prompts to ADD (bias to action) |
| Added persistence language | "Persist until fully handled end-to-end" | gpt-5.3-codex.md → Key Prompts to ADD |
| Added bias to action | "Default to implementing with reasonable assumptions" | gpt-5.3-codex.md → Key Prompts to ADD |
| Added tool preferences | "rg over grep; dedicated tools over shell" | gpt-5.3-codex.md → Key Prompts to ADD |
| Added code quality criteria | "Correctness, clarity, reliability + codebase conventions" | gpt-5.3-codex.md → Key Prompts to ADD |
