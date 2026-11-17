---
layout: default
---

# 08_ForLoops_ComponentChecklist

**Difficulty:** Medium  
**Primary Python Concept:** `for` loops over collections  
**Supporting Concepts:** Lists, strings, sets, validation, filtering  
**Automotive Domain:** Manufacturing component inspection  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Process an inspection checklist and identify incomplete or failed components.

## Prerequisites
Lists, strings, loops, sets, functions, and validation.

## Scenario Introduction
A factory inspection records each component name and result. Valid results are `PASS`, `FAIL`, and `SKIP`.

## Problem Statement
**Goal:** Process an inspection checklist and identify incomplete or failed components.

**Specifically:** Summarize the checklist while preserving the order in which failed components occurred.

## Task to Implement
Implement `inspect_components(records: list[tuple[str, str]]) -> dict[str, object]`. Return `total`, `passed`, `failed_components`, and `skipped`.

## Input Specification
There are 0 to 10,000 records. Names are non-empty strings. Results are case-insensitive but must normalize to `PASS`, `FAIL`, or `SKIP`. Reject invalid records with `ValueError`.

## Output Specification
Return counts as integers and `failed_components` as a list of names in input order.

## Rules and Constraints
- Use a `for` loop.
- Preserve duplicate component names.
- Do not sort or mutate input records.

## Hints
1. Normalize each result before branching.
2. Maintain independent counters.
3. Append failed names rather than using a set.

## Common Mistakes
- Dropping duplicate failures.
- Treating lowercase results as invalid.
- Counting `SKIP` as pass.

## Extension Challenge
Return the first failed component index, or `None` when all pass.
