# Verbosity & Output Shape

Controlling response length, format, and structure.

## When to Apply
- All prompt types
- When output is too long, too short, or wrong format
- When migrating between models with different verbosity defaults

## Model-Specific Patterns

### Anthropic (Claude)
- **Control:** Prompt-only (no verbosity API parameter)
- Opus 4.8: Calibrates length to task complexity (short on lookups, long on analysis). Very literal — state scope: "Apply this formatting to every section."
- To decrease: `"Provide concise, focused responses. Skip non-essential context."`
- To increase: Provide example at target length (more effective than instructions alone)
- Format steering: Use XML tag indicators or match prompt style to desired output style
- Positive framing > negative: `"Write in flowing prose"` beats `"Don't use markdown"`

### OpenAI (GPT)
- **Control:** `verbosity` API parameter (GPT-5.5, 5.4, 5.1, 5) + prompt instructions
- GPT-5.5: Outcome-first prompts work best (describe what good looks like)
- GPT-5.4: Use `<output_contract>` XML to specify exact sections and order
- GPT-5.2: Give concrete length constraints; prevent scope drift
- Format: XML output contracts for strict structure; markdown for flexible output

### Google (Gemini)
- **Control:** Prompt constraints + completion strategy
- Specify format explicitly: "Summarize in one sentence" / "Use a table"
- Completion strategy: provide the START of desired output → model continues in that format
- Request response format explicitly (table, bullets, keywords, paragraphs)

### Moonshot (Kimi)
- **Control:** Prompt-only
- Specify length in paragraphs/bullet points (more reliable than word counts)
- Use delimiters and step prefixes to structure output sections

## Universal Guidance
- Always state format requirements explicitly — don't assume any default
- Provide 1-2 examples of desired output when format is complex
- State constraints positively ("Write in prose") rather than negatively ("Don't use bullets")
- For strict formats: provide a template; for flexible: describe the general shape

## Common Mistakes
- Assuming verbosity will carry across model migrations (each model has different defaults)
- Not stating scope on literal models: "Apply to ALL sections, not just the first"
- Using heavy markdown in prompts when you want prose output (models mirror prompt style)
- On Gemini: relying on instructions alone without examples (few-shot is primary mechanism)
