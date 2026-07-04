# Claude (General — Older Models)

Last-verified: 2026-07-04
Source: src-011-anthropic-general-best-practices
Covers: Opus 4.5, 4.6, 4.7; Sonnet 4.5, 4.6; Haiku 4.5

## Defaults
- Effort: Available on all current models
- Thinking: Varies by model
- Temperature: Supported on older models
- Prefills: NOT supported on 4.6+ (400 error)

## Universal Claude Patterns (All Models)
- Be clear and direct; specific about format/constraints
- Use XML tags for structure (`<instructions>`, `<context>`, `<input>`)
- Give a role in system prompt (even one sentence helps)
- Use 3-5 few-shot examples wrapped in `<example>` tags
- Put long documents at TOP of prompt (query at end: +30% quality)
- Tell Claude what to DO, not what NOT to do
- Explain WHY instructions matter (Claude generalizes from motivation)

## Key Prompts to ADD
- Role: "You are a [domain] specialist focused on [audience]."
- Document structure: `<document index="N"><source>...</source><document_content>...</document_content></document>`
- Quote grounding: "Find relevant quotes first, place in <quotes> tags, then answer."
- LaTeX control: "Do not use LaTeX. Write math with standard text characters."

## Key Prompts to REMOVE
- Prefilled assistant responses on 4.6+ models (400 error)
- Vague instructions without examples

## Anti-Patterns
- Using prefilled responses on 4.6+ → 400 error
- Not wrapping distinct content types in XML tags → misinterpretation
- Relying on model to infer intent from vague prompts
