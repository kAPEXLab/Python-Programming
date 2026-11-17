---
layout: default
---

# 27_SortingSearchingAggregationFilteringMappingReduction_PartsDemand

**Difficulty:** Difficult
**Primary Python Concept:** Sorting, searching, aggregation, filtering, mapping, and reduction  
**Supporting Concepts:** Grouping, thresholds, key functions  
**Automotive Domain:** Offline parts-demand report  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Aggregate work-order quantities and select parts that meet a demand threshold.

## Prerequisites
Dictionaries, loops, comprehensions, sorting, and validation.

## Scenario Introduction
A parts planner has completed work-order lines and wants the most requested components.

## Problem Statement
**Goal:** Aggregate work-order quantities and select parts that meet a demand threshold.

**Specifically:** Sum quantities by part and return only parts whose total meets the threshold.

## Task to Implement
Implement `parts_demand(lines: list[dict[str, object]], minimum_quantity: int) -> list[tuple[str, int]]`.

## Input Specification
Each line has `part` (non-empty string) and `quantity` (integer from 1 through 1000). The threshold is an integer from 1 through 10000.

## Output Specification
Return `(part, total_quantity)` tuples sorted by total descending, then part ascending. Include totals greater than or equal to the threshold.

## Rules and Constraints
- Reject booleans and malformed records.
- Do not mutate input.
- Return `[]` when no part reaches the threshold.

## Hints
1. Reduce quantities into a dictionary.
2. Filter dictionary items by threshold.
3. Sort tuples with negative quantity as the primary key.

## Common Mistakes
- Filtering individual lines instead of totals.
- Excluding totals equal to the threshold.
- Sorting part names before demand.

## Extension Challenge
Return the top three parts and their percentage of total demand.
