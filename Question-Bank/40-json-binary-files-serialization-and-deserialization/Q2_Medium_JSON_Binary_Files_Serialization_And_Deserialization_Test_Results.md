# 40_JSONBinaryFilesSerializationAndDeserialization_TestResults

**Difficulty:** Medium
**Primary Python Concept:** JSON, binary files, serialization, and deserialization  
**Supporting Concepts:** Nested data, schema validation, bytes, rounding  
**Automotive Domain:** Offline vehicle test-result archive  
**Estimated Completion Time:** 65 minutes

## Learning Objective
Persist nested test results while preserving deterministic numeric and list data.

## Prerequisites
JSON, dictionaries, lists, binary file modes, and validation.

## Scenario Introduction
A quality harness saves simulated test outcomes for later review.

## Problem Statement
**Goal:** Persist nested test results while preserving deterministic numeric and list data.

**Specifically:** Implement `serialize_results(results: dict[str, object]) -> bytes` and `deserialize_results(payload: bytes) -> dict[str, object]`.

## Task to Implement
Require `vehicle_id`, `passed` boolean, and `checks` list. Each check has `name` string and `score` number from 0 through 100. Serialize sorted-key JSON as UTF-8 bytes; scores must be rounded to two decimals.

## Input Specification
The vehicle ID and check names are non-empty. At least one check is required.

## Output Specification
Return bytes from serialization and the validated dictionary from deserialization.

## Rules and Constraints
- Do not use pickle.
- Reject malformed UTF-8, invalid JSON, and invalid schema with `ValueError`.
- Preserve check order.

## Hints
Decode bytes explicitly, call `json.loads`, then validate each nested check.

## Common Mistakes
- Using pickle for untrusted data.
- Validating only top-level keys.
- Rounding after serialization instead of before normalization.

## Extension Challenge
Add a binary checksum field and verify it before decoding.
