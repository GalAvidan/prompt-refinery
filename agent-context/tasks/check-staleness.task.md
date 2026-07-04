# Task: Check Staleness

## id

check-staleness

## Goal

Detect stale or TTL-expired Prompt Refinery map entries without modifying files.

## Context Priority

1. `ales.manifest.json`
2. `map/_provenance.json`

## Steps

1. Load `map/_provenance.json`.
2. For each tracked entry, mark it `STALE` when `stale` is `true`.
3. Mark an entry `TTL_EXPIRED` when `generated_at` plus `ttl_days` is older than the current time.
4. Recompute fingerprints for readable sources in `derived_from` and compare them with stored fingerprints.
5. Mark fingerprint mismatches as `STALE` with reason `source fingerprint changed`.
6. Report each entry as `FRESH`, `STALE`, or `TTL_EXPIRED` with the reason.

## Expected Output

A read-only staleness report for `modules` and `apis`.

## Stop Conditions

- `map/_provenance.json` is missing.
- A source path listed in `derived_from` cannot be interpreted as a file or glob.