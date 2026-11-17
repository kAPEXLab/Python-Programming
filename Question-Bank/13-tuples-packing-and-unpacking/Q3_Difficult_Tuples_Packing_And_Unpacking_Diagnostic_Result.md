---
layout: default
---

# 13_TuplesPackingAndUnpacking_DiagnosticResult

**Difficulty:** Difficult  
**Primary Python Concept:** Tuple packing and multiple unpacking  
**Supporting Concepts:** Nested data, validation, status rules, functions  
**Automotive Domain:** Offline diagnostic result records  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Unpack a diagnostic result, validate its fields, and repack a stable summary tuple.

## Prerequisites
Tuple operations, strings, booleans, dictionaries, validation, and exceptions.

## Scenario Introduction
An offline diagnostic tool reports `(code, severity, passed, duration_ms)` for a simulated check.

## Problem Statement
**Goal:** Unpack a diagnostic result, validate its fields, and repack a stable summary tuple.

**Specifically:** Normalize a result for a deterministic report while preserving its essential status.

## Task to Implement
Implement `normalize_diagnostic_result(result: tuple[str, str, bool, int]) -> tuple[str, str, str, int]`.

## Input Specification
`code` is 2 to 12 alphanumeric characters, case-insensitive after trimming whitespace; `severity` is `INFO`, `WARNING`, or `CRITICAL`, `passed` must be a boolean, and duration is an integer from 0 through 60,000 milliseconds.

## Output Specification
Return `(code, severity, outcome, duration_ms)`, where outcome is `"PASS"` when passed is true and `"FAIL"` otherwise. Normalize code and severity to uppercase after trimming whitespace.

## Rules and Constraints
- Unpack all input fields in one statement.
- Validate before creating the output tuple.
- Reject malformed input with `ValueError` and do not mutate it.

## Hints
1. Strip and uppercase the string fields before checking choices.
2. Check `isinstance(passed, bool)` explicitly.
3. Pack the normalized values only after validation succeeds.

## Common Mistakes
- Treating any truthy value as a boolean.
- Losing the original diagnostic code.
- Returning a dictionary instead of the requested tuple.

## Extension Challenge
Return a named tuple-like structure that also includes a human-readable status message.
