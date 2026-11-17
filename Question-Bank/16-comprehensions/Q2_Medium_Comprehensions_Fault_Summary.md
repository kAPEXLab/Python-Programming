---
layout: default
---

# 16_Comprehensions_FaultSummary

**Difficulty:** Medium  
**Primary Python Concept:** Dictionary and set comprehensions  
**Supporting Concepts:** Nested records, filtering, normalization, validation  
**Automotive Domain:** Offline diagnostic fault summary  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Use comprehensions to build a code-to-count summary from diagnostic records.

## Prerequisites
Dictionaries, sets, comprehensions, strings, and functions.

## Scenario Introduction
A simulated scan returns records containing a fault code and severity.

## Problem Statement
**Goal:** Use comprehensions to build a code-to-count summary from diagnostic records.

**Specifically:** Count only critical faults and collect their normalized codes.

## Task to Implement
Implement `summarize_critical_faults(records: list[dict[str, str]]) -> dict[str, object]`.

## Input Specification
Each record has non-empty `code` and `severity`. Severity is `INFO`, `WARNING`, or `CRITICAL`, case-insensitive. Codes use letters, digits, and hyphens.

## Output Specification
Return `counts` as a dictionary comprehension mapping each critical code to its count, and `codes` as a set comprehension of those codes. Normalize codes to uppercase.

## Rules and Constraints
- Invalid records raise `ValueError`.
- Preserve no ordering requirement for the set, but counts must be exact.
- Do not mutate input.

## Hints
1. Normalize records before building result comprehensions.
2. Count critical code occurrences in a temporary structure if needed.
3. A set comprehension naturally removes duplicate codes.

## Common Mistakes
- Counting warnings as critical.
- Leaving code case unchanged.
- Building the set from all records.

## Extension Challenge
Return a list of critical records sorted by descending code count.
