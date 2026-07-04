# Instruction Following & Steerability

How literally models follow instructions and how to steer behavior effectively.

## When to Apply
- All prompt types
- When output doesn't match intent despite clear instructions
- When migrating prompts between models with different steerability profiles

## Model-Specific Patterns

### Anthropic (Claude)
- Very literal instruction following. A single brief sentence steers most behaviors.
- Opus 4.8: Interprets prompts MORE literally than earlier models. State scope explicitly: "Apply to every section, not just the first."
- Sonnet 5: Does NOT infer unstated scope. If you mean "all files," say "all files."
- Fable 5: Follows brief instructions best. Over-specification harms performance.
- Use XML tags for structure: `<instructions>`, `<context>`, `<input>`, `<examples>`
- Tell Claude what TO DO (not what NOT to do) — positive framing is more effective.
- Explain WHY instructions matter — Claude generalizes from motivation.
- Prefilled responses: NOT supported on 4.6+ (400 error). Use instruction-based alternatives.

### OpenAI (GPT)
- GPT-5: Most steerable model ever. Surgical precision. Contradictions waste reasoning tokens.
- GPT-5.5: Outcome-first prompts; shorter instructions often work better.
- GPT-5.3 Codex: Remove ALL preambles. Direct action instructions only.
- GPT-4.1: Very literal. Single-sentence corrections are highly effective.
- Use XML specs (`<instruction_spec>`) for improved adherence on GPT-5.
- Never include contradictory instructions — extremely costly on reasoning models.

### Google (Gemini)
- Few-shot examples are the PRIMARY steering mechanism (more important than instructions)
- System instructions set global tone/behavior
- Prompts without examples are "likely less effective" per Gemini docs
- Natural language formatting preferred over XML conventions

### Moonshot (Kimi)
- Step-by-step instructions with explicit prefixes work best
- Role assignment in system message is effective
- Use delimiters (triple quotes, XML, headings) to separate input sections
- Clear numbered steps are more reliable than paragraph instructions

## Universal Guidance
- Be specific and explicit — ambiguity costs quality on every model
- Match instruction style to model: XML for Claude, examples for Gemini, outcome-first for GPT
- State scope explicitly — don't rely on models to generalize from one case
- Remove contradictions before adding new instructions

## Common Mistakes
- Writing vague instructions expecting models to infer intent
- Using prefilled responses on Claude 4.6+ (400 error)
- Including contradictory instructions on GPT (wastes reasoning tokens)
- Relying on zero-shot instructions for Gemini (always add examples)
- Over-specifying for Fable 5 (does better with less instruction)
