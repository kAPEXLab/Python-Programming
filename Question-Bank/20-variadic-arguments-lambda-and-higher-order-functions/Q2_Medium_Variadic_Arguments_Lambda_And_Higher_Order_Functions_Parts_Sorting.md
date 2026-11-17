---
layout: default
---

# 20_VariadicArgumentsLambdaAndHigherOrderFunctions_PartsSorting

**Difficulty:** Medium  
**Primary Python Concept:** Higher-order functions and key lambdas  
**Supporting Concepts:** `*args`, tuples, stable sorting, validation  
**Automotive Domain:** Offline parts sorting  
**Estimated Completion Time:** 40 minutes

## Learning Objective
Sort a variable number of part records using a lambda key and deterministic tie behavior.

## Prerequisites
Functions, `*args`, tuples, lambdas, sorting, and validation.

## Scenario Introduction
A simulated workshop receives part records as `(part_number, price)` tuples.

## Problem Statement
**Goal:** Sort a variable number of part records using a lambda key and deterministic tie behavior.

**Specifically:** Return parts ordered by price ascending, then part number alphabetically.

## Task to Implement
Implement `sort_parts(*parts: tuple[str, float]) -> list[tuple[str, float]]`.

## Input Specification
Each part number is 1 to 20 uppercase alphanumeric or hyphen characters after trimming. Prices are finite numbers from 0.01 through 100000.0.

## Output Specification
Return a new list sorted by `(price, normalized_part_number)`. Normalize part numbers to uppercase and round prices to two decimals in the output.

## Rules and Constraints
- Use a lambda as the sort key.
- Preserve duplicate records and do not mutate input tuples.
- Raise `ValueError` for malformed parts.

## Hints
1. Normalize and validate before sorting.
2. Use a two-item tuple as the lambda key.
3. Keep the returned records separate from the input records.

## Common Mistakes
- Sorting by part number before price.
- Letting input case affect ties.
- Returning a tuple of records instead of a list.

## Extension Challenge
Add a keyword-only `reverse_price` option without reversing alphabetical tie order.
