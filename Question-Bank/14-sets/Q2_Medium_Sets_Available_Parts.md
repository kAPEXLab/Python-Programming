# 14_Sets_AvailableParts

**Difficulty:** Medium  
**Primary Python Concept:** Set difference and intersection  
**Supporting Concepts:** Strings, normalization, validation, functions  
**Automotive Domain:** Simulated workshop parts availability  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Use set operations to identify requested parts that are unavailable.

## Prerequisites
Sets, lists, strings, functions, and validation.

## Scenario Introduction
A workshop simulation compares parts requested for a service job with the parts currently on hand.

## Problem Statement
**Goal:** Use set operations to identify requested parts that are unavailable.

**Specifically:** Return the missing parts, available requested parts, and whether the job can start.

## Task to Implement
Implement `check_parts_availability(requested: list[str], available: list[str]) -> dict[str, object]`.

## Input Specification
Each list has 0 through 500 non-empty part names. Names use letters, digits, and hyphens; matching is case-insensitive after trimming.

## Output Specification
Return `missing` as `requested_set - available_set`, `available_requested` as their intersection, and `ready` as whether missing is empty. Values must be normalized uppercase sets.

## Rules and Constraints
- Use set difference and intersection operators.
- Duplicate entries do not affect results.
- Raise `ValueError` for malformed names and do not mutate lists.

## Hints
1. Normalize each list into a set.
2. Difference finds requested items absent from stock.
3. Use `not missing` for the readiness flag.

## Common Mistakes
- Treating duplicates as separate inventory.
- Comparing names before normalization.
- Reporting unrelated available stock as requested.

## Extension Challenge
Return the missing parts in deterministic sorted-list form as an additional field.
