# Universal Prompt Patterns

Fallback guidance for models without a dedicated reference file. Apply these patterns when the target model is unknown, undocumented, or when doing a general-purpose refinement.

## Always Apply

1. **Be specific and explicit** — State exactly what you want; avoid vague instructions
2. **Define completion criteria** — Tell the model what "done" looks like
3. **Use structured delimiters** — XML tags or markdown headings to separate concerns
4. **Remove legacy over-specification** — Delete old scaffolding from prior model generations
5. **Provide intent/context** — Explain WHY you're asking (models generalize from motivation)
6. **Don't default to max effort** — Start at medium; escalate only if quality requires it
7. **Self-verify on long runs** — Ask the model to check its work periodically
8. **Enable autonomy with clear boundaries** — Say what it CAN do, what it MUST NOT do

## General Refinement Checklist

- [ ] Is the prompt specific enough that only one interpretation is valid?
- [ ] Are format requirements stated explicitly (not assumed)?
- [ ] Is there a role or context sentence? (Even one line helps most models)
- [ ] Are examples provided for ambiguous output formats?
- [ ] Are contradictory instructions removed?
- [ ] Is the prompt structured (sections/headers) rather than a wall of text?
- [ ] Does it state what TO DO rather than what NOT to do?

## When in Doubt

- **For format control:** Provide 1-2 examples of desired output
- **For tone/style:** Give a one-sentence role ("You are a senior engineer reviewing code")
- **For length:** State explicitly ("Reply in 2-3 sentences" or "Provide a detailed analysis")
- **For accuracy:** Add "If unsure, say so" or "Cite sources"
- **For multi-step tasks:** Number the steps; ask for one step at a time or all at once

## Model-Family Heuristics

If you know the model family but not the exact version:
- **Claude-family:** Use XML tags for structure; be direct; brief instructions steer well
- **GPT-family:** Define personality; use structured delimiters; avoid contradictions
- **Gemini-family:** Lean heavily on few-shot examples; use completion strategy
- **Open-source (Llama, Mistral, etc.):** Be more explicit; provide more examples; simpler instructions
