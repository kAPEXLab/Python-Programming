# 15_Dictionaries_PartsInventory

**Difficulty:** Difficult  
**Primary Python Concept:** Dictionary aggregation  
**Supporting Concepts:** Nested records, validation, sorting, rounding, functions  
**Automotive Domain:** Simulated parts inventory report  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Aggregate quantities and values from nested inventory records into a deterministic report.

## Prerequisites
Dictionaries, lists, loops, arithmetic, sorting, and validation.

## Scenario Introduction
An offline parts fixture contains repeated records for part numbers, unit prices, and quantities.

## Problem Statement
**Goal:** Aggregate quantities and values from nested inventory records into a deterministic report.

**Specifically:** Combine duplicate parts and identify the highest-value inventory item.

## Task to Implement
Implement `summarize_parts_inventory(records: list[dict[str, object]]) -> dict[str, object]`.

## Input Specification
Each record has non-empty string `part_number`, positive finite `unit_price` from 0.01 through 100000.0, and integer `quantity` from 1 through 10000. A part must always use the same unit price.

## Output Specification
Return `quantities` as a dictionary by part number, `total_value` rounded to two decimals, and `highest_value_part` as the lexicographically smallest part on ties, or `None` for empty input.

## Rules and Constraints
- Aggregate quantity before calculating each part's value.
- Reject malformed records or conflicting prices with `ValueError`.
- Do not mutate records.

## Hints
1. Track quantity and unit price separately by part.
2. Compute value after aggregation.
3. Use a stable key rule when values tie.

## Common Mistakes
- Calculating only the last duplicate quantity.
- Rounding each line before totaling.
- Choosing a nondeterministic tie result.

## Extension Challenge
Return all parts sorted by descending inventory value and then part number.
