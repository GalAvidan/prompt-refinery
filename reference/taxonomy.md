# Prompt Technique Taxonomy

10 categories of prompt techniques. When refining a prompt, identify which categories are relevant based on the prompt type and apply model-specific patterns from the corresponding technique file.

## 1. Effort & Reasoning Control
Calibrating the model's thinking depth vs. cost/latency.
Applies to: all prompt types (especially agentic, system-prompt)

## 2. Verbosity & Output Shape
Controlling response length, format, and structure.
Applies to: all prompt types

## 3. Agentic Persistence & Autonomy
Keeping the model working through multi-step tasks.
Applies to: agentic, system-prompt

## 4. Tool Use Patterns
When/how models should use tools vs. reason internally.
Applies to: agentic, system-prompt, skill-instruction

## 5. Instruction Following & Steerability
How literally models follow instructions.
Applies to: all prompt types

## 6. Subagents & Delegation
Parallel execution and task decomposition.
Applies to: agentic, skill-instruction

## 7. Memory & Context Management
Handling long sessions and persistent knowledge.
Applies to: agentic, system-prompt

## 8. Communication Style & Personality
Tone, warmth, readability, user-facing updates.
Applies to: system-prompt, creative, one-liner

## 9. Code Generation & Editing
Producing, reviewing, and modifying code.
Applies to: agentic, structured-output

## 10. Self-Verification & Grounding
Ensuring correctness, preventing hallucination.
Applies to: all prompt types (especially structured-output, agentic)
