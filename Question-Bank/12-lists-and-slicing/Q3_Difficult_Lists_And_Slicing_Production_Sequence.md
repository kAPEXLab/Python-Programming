# 12_ListsAndSlicing_ProductionSequence

**Difficulty:** Difficult  
**Primary Python Concept:** Extended list slicing and copy semantics  
**Supporting Concepts:** Validation, transformations, tuples, rounding  
**Automotive Domain:** Offline production station sequence  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Use extended slices to inspect station batches while producing a validated, non-mutating sequence report.

## Prerequisites
Lists, slicing, dictionaries, tuples, functions, and exceptions.

## Scenario Introduction
A factory simulation records station cycle times in seconds. Consecutive records belong to a repeating three-station cycle: weld, paint, and inspection.

## Problem Statement
**Goal:** Use extended slices to inspect station batches while producing a validated, non-mutating sequence report.

**Specifically:** Return the station-specific samples, their rounded averages, and whether the sequence is complete.

## Task to Implement
Implement `analyze_production_sequence(cycle_times: list[float]) -> dict[str, object]`.

## Input Specification
The list has 0 through 300 finite values from 1.0 through 600.0 seconds. Values are measured to at most two decimals. A complete sequence has a length divisible by three.

## Output Specification
Use slices `[0::3]`, `[1::3]`, and `[2::3]`. Return `weld_times`, `paint_times`, `inspection_times`, `averages`, and `complete`. `averages` maps each station name to a value rounded to two decimals; an empty station average is `None`.

## Rules and Constraints
- Station names are `weld`, `paint`, and `inspection`.
- `complete` is true only when the list length is divisible by three.
- Raise `ValueError` for non-finite or out-of-range values.
- Do not mutate input or use sorting.

## Hints
1. Validate values before slicing.
2. Extended slices select every third item from different offsets.
3. Compute `complete` from the length, not from the contents.

## Common Mistakes
- Using a step of two.
- Dropping the incomplete tail instead of reporting it.
- Returning averages with inconsistent rounding.

## Extension Challenge
Return the longest station time and its zero-based original index.
