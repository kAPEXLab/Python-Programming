# 10_LoopControl_TestStubs

**Difficulty:** Difficult  
**Primary Python Concept:** `pass`, `continue`, and `break`  
**Supporting Concepts:** Test case processing, validation, reporting, dictionaries  
**Automotive Domain:** Offline automotive test runner  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Use all three loop-control statements deliberately while building a deterministic test-run summary.

## Prerequisites
Loops, dictionaries, functions, conditionals, validation, and formatted results.

## Scenario Introduction
An offline test runner receives test cases. `TODO` cases are placeholders, invalid cases are skipped, and `STOP` ends the run. Valid cases have a boolean `passed` field.

## Problem Statement
**Goal:** Use all three loop-control statements deliberately while building a deterministic test-run summary.

**Specifically:** Summarize executed, skipped, placeholder, and failed test cases before the stop marker.

## Task to Implement
Implement `run_test_plan(cases: list[dict[str, object]]) -> dict[str, object]`. Return `executed`, `passed`, `failed_ids`, `skipped`, and `placeholders`.

## Input Specification
Each case has `id` and `kind`. Kinds are `TEST`, `TODO`, `STOP`, or anything invalid. `TEST` requires boolean `passed`; IDs must be non-empty strings. Invalid cases are skipped. Input length is 0 to 10,000.

## Output Specification
`executed` counts valid `TEST` cases, `passed` counts passing tests, `failed_ids` preserves order, `skipped` counts invalid cases, and `placeholders` counts `TODO`. `STOP` is not counted and ends processing.

## Rules and Constraints
- Use `pass` in the `TODO` branch, `continue` for invalid cases, and `break` for `STOP`.
- A boolean is required for `passed`; do not accept integers as substitutes.
- Do not mutate input.

## Hints
1. Handle `STOP` before ordinary validation.
2. Keep a separate branch for placeholders.
3. Invalid cases should increment one counter and continue.

## Common Mistakes
- Counting `TODO` as executed.
- Processing cases after `STOP`.
- Treating `1` as the boolean `True`.

## Extension Challenge
Return the ID of the last executed test, or `None` when no test ran.
