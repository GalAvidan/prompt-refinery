# Example: Structured Output Refined for Kimi
Target: Kimi  |  Type: structured-output

## Before (Original — Generic Prompt)

```
Extract the key information from this article and return it as JSON. Include the 
title, author, date, main argument, and supporting evidence. Be accurate.
```

## After (Refined for Kimi)

```
Role: You are a precise information extraction specialist.

Task: Extract structured data from the article below.

Step 1: Read the article carefully and identify the metadata fields.
Step 2: Identify the main argument (one sentence).
Step 3: List supporting evidence (direct quotes only).
Step 4: Format your output as the JSON structure shown below.

Output format:
{
  "title": "exact title from article",
  "author": "author name",
  "date": "YYYY-MM-DD",
  "main_argument": "one sentence summarizing the core claim",
  "evidence": [
    "direct quote 1",
    "direct quote 2",
    "direct quote 3"
  ]
}

Important: If any field cannot be found in the article, use "NOT FOUND" as the value. 
Do not guess or infer information that is not explicitly stated.

---

Article:
"""
[ARTICLE TEXT HERE]
"""
```

## Changes Applied

| Change | Reason | Source |
|--------|--------|--------|
| Added explicit role assignment | Role in system message is effective for Kimi | kimi.md → Key Prompts to ADD |
| Added numbered steps with prefixes | Step-by-step with explicit prefixes works best | kimi.md → Key Prompts to ADD |
| Added triple-quote delimiters | Delimiters separate input sections clearly | kimi.md → Key Prompts to ADD |
| Added "NOT FOUND" instruction | Reference text pattern: state what to do if not found | kimi.md → Key Prompts to ADD |
| Added explicit output format example | Kimi needs concrete format demonstration | kimi.md → Key Prompts to ADD |
| Removed vague "be accurate" | Replaced with concrete grounding instruction | kimi.md → Anti-Patterns |
| Separated instructions from input | Clear delimiter between task and reference text | kimi.md → Key Prompts to ADD (delimiters) |
