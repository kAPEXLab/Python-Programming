---
layout: default
---

# 37_BuiltInExceptionsAndTryExcept_InvalidSensorValue

**Difficulty:** Easy
**Primary Python Concept:** Built-in exceptions and try-except  
**Supporting Concepts:** Parsing, validation, loops, error reporting  
**Automotive Domain:** Offline sensor packet parsing  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Convert untrusted sensor text while handling expected built-in exceptions.

## Prerequisites
Functions, strings, lists, `try-except`, and `ValueError`.

## Scenario Introduction
A simulated packet contains textual temperature values that may be malformed.

## Problem Statement
**Goal:** Convert untrusted sensor text while handling expected built-in exceptions.

**Specifically:** Implement `parse_temperatures(raw_values: list[str]) -> tuple[list[float], list[str]]`, converting Celsius strings and collecting invalid entries.

## Task to Implement
Strip whitespace, convert with `float`, accept values from -50 through 150 inclusive, and round valid results to one decimal place. Invalid entries are returned unchanged in the error list.

## Input Specification
The input list may be empty. Items should normally be strings; non-strings are invalid entries.

## Output Specification
Return `(valid_values, invalid_values)` preserving input order within each list.

## Rules and Constraints
- Catch expected conversion and type errors without hiding programming errors.
- Never stop processing after one bad value.
- Use Python 3.12+.

## Hints
Keep conversion and range validation inside the loop.

## Common Mistakes
- Catching every exception with a bare `except`.
- Returning converted out-of-range values.
- Losing the original invalid text.

## Extension Challenge
Return an error dictionary containing index and reason.
