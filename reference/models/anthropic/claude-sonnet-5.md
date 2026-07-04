# Claude Sonnet 5

Last-verified: 2026-07-04
Source: src-002-anthropic-sonnet-5

## Defaults
- Effort: high (medium ≈ old Sonnet 4.6 at high)
- Thinking: Adaptive, ON by default
- Temperature: ❌ REJECTS non-default values (400 error)
- Tokenizer: New, produces ~30% more tokens — adjust max_tokens

## Strengths
- Coding and agentic tasks
- Tool-eager (reaches for tools readily)
- Very literal instruction following
- Good cost/performance balance

## Key Prompts to ADD
- Scope statement: "Apply this formatting to every section, not just the first one"
- For design: Specify concrete alternative OR propose 4 directions before building
- Code review: "Report every issue including low-severity. Your goal is coverage."
- Anti-generic aesthetic: "NEVER use generic AI aesthetics (Inter, Roboto, purple gradients)"

## Key Prompts to REMOVE
- temperature/top_p/top_k parameters (400 error)
- Old forced-status scaffolding ("After every 3 tool calls, summarize")
- Manual extended thinking budget (not supported, 400 error)

## Anti-Patterns
- Setting temperature → 400 error
- Expecting inference of unstated scope → model is very literal
- Relying on `thinking: {type: "enabled", budget_tokens: N}` → removed
