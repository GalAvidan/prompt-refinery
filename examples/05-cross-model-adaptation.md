# Example: Cross-Model Adaptation (Claude → GPT)
Target: GPT-5.4 (adapted from Claude Opus 4.8)  |  Type: skill-instruction

## Before (Original — Written for Claude Opus 4.8)

```xml
<instructions>
You are a financial analyst reviewing quarterly earnings reports.

<effort>xhigh</effort>
<thinking type="adaptive"/>

Use tools when not sure — don't reason from incomplete data. Spawn subagents when 
fanning out across multiple documents. Audit each claim against a tool result.

Report every issue including low-severity. Your goal is coverage.

<output>
Lead with the outcome. Provide executive summary first, then supporting evidence 
with quotes from source documents.
</output>
</instructions>
```

## After (Refined for GPT-5.4)

```xml
<instruction_spec>
You are a financial analyst reviewing quarterly earnings reports.

<output_contract>
Return exactly these sections in order:
1. Executive Summary (3-5 sentences, key findings only)
2. Revenue Analysis (with source citations)
3. Risk Factors (ranked by severity)
4. Recommendations (actionable, numbered)
</output_contract>

<verbosity_controls>
Prefer concise, information-dense writing. Use data over narrative.
Evidence format: "[metric] was [value] (Source: [document], p.[page])"
</verbosity_controls>

<follow_through_policy>
If the intent is clear and the next step is reversible, proceed without asking.
Verify claims against source documents before including them.
For each finding: state the claim, cite the evidence, note confidence level.
</follow_through_policy>

<reasoning_effort>medium</reasoning_effort>
</instruction_spec>
```

## Changes Applied

| Change | Reason | Source |
|--------|--------|--------|
| Replaced Claude `<effort>` with GPT `<reasoning_effort>` | Different parameter system | gpt-5.4.md → Defaults |
| Removed `<thinking type="adaptive"/>` | GPT has built-in reasoning (no toggle) | gpt-5.4.md → N/A for GPT |
| Removed subagent instructions | GPT uses parallel tool calls, not subagents | gpt-5.4.md → Strengths |
| Added `<output_contract>` | GPT-5.4's key pattern for structured output | gpt-5.4.md → Key Prompts to ADD |
| Added `<verbosity_controls>` | GPT-5.4 respects explicit verbosity blocks | gpt-5.4.md → Key Prompts to ADD |
| Added follow-through policy | "If intent clear and next step reversible, proceed" | gpt-5.4.md → Key Prompts to ADD |
| Added explicit verification | GPT-5.4: explicit checks before claims | gpt-5.4.md → Key Prompts to ADD |
| Set effort to medium | GPT-5.4: higher is NOT always better | gpt-5.4.md → Anti-Patterns |
| Kept XML structure | GPT-5.4 responds well to XML output contracts | gpt-5.4.md → Key Prompts to ADD |
