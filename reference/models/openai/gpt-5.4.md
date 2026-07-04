# GPT-5.4

Last-verified: 2026-07-04
Source: src-005-openai-gpt-5.4

## Defaults
- Reasoning effort: Task-dependent (not always better higher)
- Verbosity: API parameter available
- Phase: Verify `phase` field preserved in integration

## Strengths
- Multi-step execution robustness
- Tone adherence with less drift
- Evidence-rich synthesis
- Batched/parallel tool calling accuracy
- Spreadsheet/finance/Excel workflows

## Key Prompts to ADD
- Output contract: `<output_contract>Return exactly sections requested, in order.</output_contract>`
- Verbosity: `<verbosity_controls>Prefer concise, information-dense writing.</verbosity_controls>`
- Follow-through: "If intent clear and next step reversible, proceed without asking."
- Verification: Explicit checks before irreversible actions

## Key Prompts to REMOVE
- Assumptions that higher effort = better (depends on task shape)

## Anti-Patterns
- Not defining output contract → verbose/unstructured output
- Missing phase field in integration → intermediate update treated as final answer
- Vague "be thorough" without scope → over-exploration
