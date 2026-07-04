# Claude Opus 4.8

Last-verified: 2026-07-04
Source: src-003-anthropic-opus-4.8

## Defaults
- Effort: Start at xhigh (more important than any prior Opus)
- Thinking: OFF unless set to adaptive
- Temperature: Supported
- Token budget: At max/xhigh, set 64k+ max output tokens

## Strengths
- Long-horizon agentic work, knowledge work, vision, memory
- Bug-finding (higher recall AND precision)
- Direct, opinionated style
- Strong design instincts

## Key Prompts to ADD
- Tool encouragement: "Use tools when not sure; don't reason from incomplete data"
- Subagent guidance: "Spawn multiple subagents when fanning out across items"
- Design direction: Specify concrete palette/fonts/layout OR propose options
- Thinking opt-in: Set `thinking: {type: "adaptive"}` if needed

## Key Prompts to REMOVE
- "Be conservative" in code review (follows too faithfully → lower recall)
- Generic design instructions ("don't use cream") → shifts to different fixed palette

## Anti-Patterns
- Defaulting to max effort (diminishing returns, can overthink)
- Expecting eager tool use (favors reasoning over tools)
- Expecting many subagents by default (spawns fewer)
