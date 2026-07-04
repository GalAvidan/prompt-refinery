# Example: Creative Prompt Refined for Gemini
Target: Gemini  |  Type: creative

## Before (Original Prompt)

```xml
<system>
You are a creative writing assistant. Generate engaging blog post introductions.
Use a conversational tone. Keep it under 100 words.
</system>
```

## After (Refined Prompt)

```
You are a tech blog writer for a developer audience.

Generate engaging blog post introductions. Use a conversational, slightly irreverent 
tone. Keep introductions to 2-3 sentences (under 80 words).

Here are examples of the style I want:

Example 1:
Topic: "Kubernetes scaling"
Output: "Your cluster's fine at 3am. By 9am it's on fire. Here's how to make 
auto-scaling actually work before your on-call rotation becomes a therapy session."

Example 2:
Topic: "TypeScript generics"
Output: "Generics look scary until you realize they're just functions for types. 
Let's build three real patterns you'll use every week — no PhD required."

Example 3:
Topic: "API rate limiting"
Output: "You shipped without rate limiting. Congratulations, you now have a DDoS 
vulnerability disguised as a feature. Let's fix that in 20 lines."

Now write an introduction for this topic:
[USER TOPIC HERE]
```

## Changes Applied

| Change | Reason | Source |
|--------|--------|--------|
| Removed XML tags | Not native to Gemini; natural language formatting preferred | gemini.md → Key Prompts to REMOVE |
| Added 3 few-shot examples | Few-shot is Gemini's PRIMARY steering mechanism | gemini.md → Key Prompts to ADD |
| Added specific constraints | "2-3 sentences, under 80 words" — explicit format control | gemini.md → Key Prompts to ADD |
| Added audience specification | Grounds tone in context rather than abstract description | gemini.md → Key Prompts to ADD |
| Used completion strategy | "Now write an introduction for:" prompts continuation | gemini.md → Key Prompts to ADD (completion strategy) |
| Removed effort/reasoning params | Don't exist for Gemini | gemini.md → Key Prompts to REMOVE |
