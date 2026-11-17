---
layout: default
---

# 14_Sets_UniqueFaultCodes

**Difficulty:** Easy  
**Primary Python Concept:** Sets and uniqueness  
**Supporting Concepts:** Strings, normalization, validation, functions  
**Automotive Domain:** Offline diagnostic fault codes  
**Estimated Completion Time:** 25 minutes

## Learning Objective
Use a set to count unique normalized fault codes.

## Prerequisites
Lists, strings, sets, functions, and exceptions.

## Scenario Introduction
A simulated scan may report the same diagnostic trouble code several times.

## Problem Statement
**Goal:** Use a set to count unique normalized fault codes.

**Specifically:** Return the unique codes in uppercase and the number of distinct codes.

## Task to Implement
Implement `unique_fault_codes(codes: list[str]) -> dict[str, object]`.

## Input Specification
The list has 0 through 1,000 non-empty strings. Codes may contain letters, digits, and hyphens, and surrounding whitespace is allowed.

## Output Specification
Return `unique_codes` as a set of uppercase trimmed codes and `unique_count` as its size.

## Rules and Constraints
- Use a set for uniqueness.
- Reject empty or malformed codes with `ValueError`.
- Do not mutate input.

## Hints
1. Strip and uppercase each code.
2. Add normalized values to a set.
3. Check allowed characters before insertion.

## Common Mistakes
- Counting list entries instead of unique values.
- Forgetting whitespace normalization.
- Returning a sorted list when a set is requested.

## Extension Challenge
Return a dictionary mapping each normalized code to its occurrence count.
