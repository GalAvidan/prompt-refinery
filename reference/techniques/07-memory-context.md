# Memory & Context Management

Handling long sessions, persistent knowledge, and multi-window workflows.

## When to Apply
- Prompt types: agentic, system-prompt
- Tasks exceeding a single context window
- Long conversations requiring state tracking
- Multi-document analysis (20k+ tokens)

## Model-Specific Patterns

### Anthropic (Claude)
- Fable 5: Native memory file support. "Store one lesson per file with a one-line summary at the top." Can work across context windows with state saved to files.
- All Claude: Put long documents at TOP of prompt, query at end (+30% quality). Wrap documents in XML: `<document index="N"><source>...</source><document_content>...</document_content></document>`
- Context compaction: "Do not stop early due to token budget. Save state before context refreshes."
- Quote grounding: "Find relevant quotes first, place in `<quotes>` tags, then answer."

### OpenAI (GPT)
- GPT-5: Responses API with `previous_response_id` for reasoning persistence across turns
- GPT-5.3 Codex: First-class compaction support for multi-hour sessions
- GPT-5.4: Evidence-grounded synthesis; re-ground the model in long conversations
- Pattern: Markdown degrades over long conversations → re-instruct formatting every 3-5 messages

### Google (Gemini)
- Not specifically documented for memory/persistence
- For long documents: use system instructions for persistent context
- Structured output API handles schema persistence

### Moonshot (Kimi)
- For long dialogs: summarize previous rounds to stay within context length
- For long documents: chunk and recursively summarize (summary of summaries)
- Include preceding chapter summaries when understanding requires earlier context
- Fixed context length — must manage actively via summarization

## Universal Guidance
- Structure state in three formats: JSON (structured data), text (progress notes), git (history)
- For multi-window tasks: save state before context fills; read state on resume
- For large documents: put data at top, instructions at bottom; use XML wrappers
- Encourage quote-then-answer pattern for accuracy on long-context inputs

## Common Mistakes
- On Fable 5: showing remaining-token counts → triggers premature session ending
- Not re-grounding format instructions in long GPT conversations → format drift
- On Kimi: long unbroken conversations without summarization → context overflow
- Putting instructions above long documents (worse quality than documents-first)
