---
layout: default
---

# 09_WhileLoops_DiagnosticRetries

**Difficulty:** Medium  
**Primary Python Concept:** `while` loops with bounded retries  
**Supporting Concepts:** Lists, booleans, validation, early termination  
**Automotive Domain:** Offline diagnostic retry simulation  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Use a bounded `while` loop to retry simulated diagnostic responses safely.

## Prerequisites
Lists, loops, booleans, functions, and exceptions.

## Scenario Introduction
A diagnostic tool may retry a request when a simulated response is `TIMEOUT`. A successful response is `OK`; any other response is a failure.

## Problem Statement
**Goal:** Use a bounded `while` loop to retry simulated diagnostic responses safely.

**Specifically:** Return the response outcome and number of attempts used.

## Task to Implement
Implement `run_diagnostic_retries(responses: list[str], max_attempts: int) -> tuple[str, int]`.

## Input Specification
Responses contain 1 to 100 labels, each `OK`, `TIMEOUT`, or `ERROR`, case-insensitive. `max_attempts` is 1 through 100 and cannot exceed the response count. Reject invalid input with `ValueError`.

## Output Specification
Return `("SUCCESS", attempts)` at the first `OK`; return `("FAILED", attempts)` after the first non-timeout failure or after the retry limit. Attempts count inspected responses.

## Rules and Constraints
- Use a `while` loop.
- Stop as soon as success or permanent failure occurs.
- Do not retry `ERROR`.

## Hints
1. Track both index and attempts.
2. Stop on `OK` or `ERROR`.
3. The loop condition should include the retry limit.

## Common Mistakes
- Retrying after `ERROR`.
- Reading past the response list.
- Ignoring `max_attempts`.

## Extension Challenge
Return the normalized response history that was actually inspected.
