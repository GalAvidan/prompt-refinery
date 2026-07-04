# Kimi (Moonshot AI)

Last-verified: 2026-07-04
Source: src-013-kimi-moonshot-prompting
Covers: All Kimi models (K2.7 Code, etc.)

## Defaults
- No effort/reasoning parameter
- Temperature: Supported
- Context: Fixed length (manage via summarization)
- Default system prompt includes safety boundaries

## Strengths
- Clear instruction following with explicit steps
- Reference text grounding ("answer from article")
- Role assignment effectiveness
- Delimiter-based input separation

## Key Prompts to ADD
- Role: Assign via system message (detailed persona)
- Delimiters: Triple quotes, XML tags, or section headings to separate input parts
- Steps: "Step one: ... Step two: ..." with output prefixes
- Reference text: "Answer using provided article. If not found, write 'I can't find the answer.'"
- Length: Specify in paragraphs/bullet points (more reliable than word counts)
- Few-shot: Provide examples when style is hard to describe explicitly

## Key Prompts to REMOVE
- Complex agentic patterns (not supported)
- Multi-turn persistence prompts (single-turn focused)
- Effort/reasoning parameters (don't exist)
- Subagent dispatch instructions (not applicable)

## Anti-Patterns
- Expecting agentic multi-step behavior → use explicit step decomposition instead
- Long unbroken conversations → summarize and chunk to stay within context
- Exact word count targets → use paragraphs/bullets instead

## Context Management
- For long dialogs: summarize previous rounds to stay within context length
- For long documents: chunk and recursively summarize (summary of summaries)
- Include preceding chapter summaries when understanding requires earlier context
