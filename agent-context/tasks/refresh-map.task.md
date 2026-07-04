# Task: Refresh Map

## id

refresh-map

## Goal

Re-derive the Prompt Refinery `map/` files from current Markdown source and update `map/_provenance.json`.

## Context Priority

1. `ales.manifest.json`
2. `map/_provenance.json`
3. `SKILL.md`
4. `index.md`
5. `agent.md`
6. `reference/taxonomy.md`

## Steps

1. Load `map/_provenance.json` and identify tracked map entries.
2. For `modules`, inspect the tracked Markdown globs for `SKILL.md`, `README.md`, `index.md`, `agent.md`, `examples/`, and `reference/`.
3. Rebuild `map/modules.json` only from current project-specific files and keep entries aligned with the existing logical groups.
4. Keep `map/apis.json` as `[]` unless the repository adds a real REST, GraphQL, gRPC, event, or CLI surface.
5. Recompute fingerprints for refreshed entries.
6. Update `map/_provenance.json` with the new timestamp, fingerprints, `stale: false`, and `stale_reason: null`.
7. Update `ales.manifest.json` with the new `updated_at` timestamp and current `repo_sha`.
8. Report which files were refreshed and which were unchanged.

## Expected Output

The ALES map files reflect the current Prompt Refinery Markdown structure, and `_provenance.json` marks all entries fresh.

## Stop Conditions

- A tracked source file or folder cannot be read.
- A current source pattern contradicts the existing module grouping and cannot be mapped without human judgment.
- The task would require changing files under `reference/` during routine map refresh.