---
layout: default
---

# 01_PythonSyntax_TestHarnessLayout

**Difficulty:** Difficult  
**Primary Python Concept:** Python syntax and program structure  
**Supporting Concepts:** Functions, nested data, validation, exceptions, modular decomposition  
**Automotive Domain:** Offline automotive test automation  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Design a readable, multi-function Python program that validates and summarizes simulated test results.

## Prerequisites
Functions, collections, loops, conditionals, exceptions, and formatted strings.

## Scenario Introduction
A test harness runs offline checks against simulated vehicle components. Each result contains a component name, test name, status, and duration in seconds.

## Problem Statement
**Goal:** Design a readable, multi-function Python program that validates and summarizes simulated test results.

**Specifically:** Create a summary for a batch of test results, including totals, pass rate, failed test names, and total execution time.

## Task to Implement
Implement `summarize_test_batch(results: list[dict[str, object]]) -> str`. Each record must contain `component`, `test`, `status`, and `duration`. Status is `PASS` or `FAIL`. Return five lines: total tests, passed tests, pass rate, failed tests, and total duration.

## Input Specification
- `results`: 0 to 50,000 dictionaries.
- `component` and `test`: non-empty strings.
- `status`: exactly `PASS` or `FAIL`.
- `duration`: number from 0 through 3,600 seconds.
- Reject missing keys, wrong types, blank names, invalid statuses, or invalid durations with `ValueError`.

## Output Specification
Return:
`Total tests: N\nPassed: P\nPass rate: X.XX%\nFailed tests: name1, name2\nTotal duration: Y.YY s`
Use `None` on the failed-tests line when no test failed. Preserve input order for failed tests.

## Rules and Constraints
- Use Python 3.12 or later.
- Use at least two helper functions in addition to the public function.
- Do not mutate input records.
- Pass rate is `passed / total * 100`; for zero tests use `0.00%`.
- Raise `ValueError` for invalid data before returning a partial report.
- Display rates and duration to exactly two decimal places.

## Hints
- Correctness: 3 points
- Appropriate syntax and decomposition: 1 point
- Input validation: 1 point
- Edge-case handling: 1 point
- Readability and naming: 1 point
- Modularity: 1 point
- Efficiency: 0.5 point
- Documentation: 0.5 point
- Testability: 1 point

1. Validate a record in a dedicated helper before aggregating it.
2. Maintain separate counters and a list of failed test names.
3. Handle the zero-test pass-rate case explicitly.

## Common Mistakes
- Returning a partial result after encountering invalid data.
- Using dictionary keys without checking they exist.
- Losing failed-test order by converting names to a set.
- Formatting `50%` instead of `50.00%`.

## Extension Challenge
Add a per-component summary while keeping the five required lines unchanged.
