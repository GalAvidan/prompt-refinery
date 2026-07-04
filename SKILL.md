---
name: prompt-refinery
description: "Refines and optimizes a user's prompt for a specific target model (Claude, GPT, Gemini, Llama, etc.) by applying that model's documented best practices. Use when: 'optimize this prompt for X', 'refine my prompt', 'make this work better on GPT', 'rewrite for Claude', 'adapt prompt for Gemini', 'improve this prompt', 'prompt engineering help'."
---

## Quick Start

For repository navigation, start with `index.md`. For agent operating boundaries, load `agent.md`.

1. User provides a prompt and names (or the agent infers) the target model.
2. Load the model-specific reference from `./reference/models/<vendor>/<model>.md`.
3. Classify the prompt type and load matching technique files from `./reference/techniques/`.
4. Rewrite the prompt applying model-specific patterns.
5. Return the refined prompt with brief change notes.

> Files in `./reference/` are read-only reference data. Do not modify them during execution.

## When to Use

- User asks to "optimize", "refine", "improve", or "rewrite" a prompt
- User specifies a target model or agent mode
- User wants to adapt an existing prompt for a different model
- User is drafting a system prompt, skill, or instruction set for a specific engine

## Procedure

1. **Identify target model**
   - Explicit: user states "for Claude Fable 5" / "for GPT-4.1"
   - Inferred: from active agent mode, system prompt context, or conversation
   - If ambiguous, ask: "Which model will this prompt run on?"
   - If model is not documented, load `./reference/universal.md` and apply general patterns

2. **Classify prompt type**
   - `one-liner` — short user message (1-3 sentences)
   - `system-prompt` — system-level instruction block
   - `skill-instruction` — SKILL.md or agent instruction set
   - `agentic` — tool use, multi-step workflow, autonomous agent
   - `creative` — open-ended generation (writing, brainstorming)
   - `structured-output` — JSON, code, formatted data extraction
   - If a prompt spans multiple types, treat the primary type as structural; load secondary technique files additively.

3. **Load references**
   - Primary: `./reference/models/<vendor>/<model>.md`
   - Technique files matching prompt type from `./reference/techniques/` (use taxonomy.md to identify relevant categories)
   - Cross-model matrix for quick divergence checks: `./reference/cross-model-matrix.md`

4. **Apply model-specific refinements**
   - Restructure formatting (XML tags for Claude, markdown for GPT, etc.)
   - Adjust verbosity/tone per model preferences
   - Add model-specific patterns (effort levels, reasoning guidance, tool instructions)
   - Remove patterns that harm performance on the target model
   - Preserve user intent — never change what the prompt asks for

5. **Output**
   - The refined prompt (ready to use)
   - Brief notes: what changed and why (referencing model docs)

6. **Self-verify**
   - Re-read the model file. Confirm every applied pattern is cited there.
   - Remove any pattern that conflicts with the target model.
   - Confirm the original intent is preserved and output is usable as-is (no placeholders).

## Reference

- `./reference/taxonomy.md` — prompt technique categories
- `./reference/cross-model-matrix.md` — technique × model lookup (start here for quick comparisons)
- `./reference/universal.md` — fallback patterns for unknown/undocumented models
- `./reference/models/<vendor>/` — per-model best practices (anthropic, openai, google, moonshot)
- `./reference/techniques/` — per-technique deep dives (one file per taxonomy category)
- `./examples/` — before/after refinement demonstrations
