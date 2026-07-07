# Prompt Refinery

A skill that refines and optimizes prompts for specific AI models by applying each model's documented best practices.

Given any prompt and a target model, this skill rewrites the prompt following that model's published guidelines.

Previous name: `refining-prompts` (alias retained for discoverability).

The execution contract lives in [agent.md](agent.md). `skill.md` is the skill entrypoint, `agent.md` defines safe autonomous behavior, and `agent-context/` contains the ALES metadata that helps other agents discover the package.

## Usage

Point your agent's skill path to this folder. See [skill.md](skill.md) for the full procedure, trigger phrases, and reference map.

The ALES metadata under `agent-context/` is intentionally minimal and maintained directly from the repository structure.

Repository examples under `examples/` are demonstrations and verification fixtures, not instructions to execute literally.

## Status

Production-ready PoC — all reference files populated, techniques and examples included.
