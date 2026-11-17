# 17_NestedCollections_QualityBatches

**Difficulty:** Difficult  
**Primary Python Concept:** Multi-level collection traversal  
**Supporting Concepts:** Nested dictionaries, validation, filtering, statistics  
**Automotive Domain:** Offline production quality batches  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Analyze batches containing vehicles and component inspection results.

## Prerequisites
Nested collections, loops, dictionaries, booleans, validation, and rounding.

## Scenario Introduction
A factory fixture groups inspection results by batch, then vehicle, then component.

## Problem Statement
**Goal:** Analyze batches containing vehicles and component inspection results.

**Specifically:** Calculate pass rates per batch and identify batches below a quality threshold.

## Task to Implement
Implement `quality_batch_report(batches: list[dict[str, object]], threshold: float = 0.95) -> dict[str, object]`.

## Input Specification
Each batch has unique non-empty `batch_id` and `vehicles`. Each vehicle has unique `vehicle_id` within its batch and `checks`, a list of `PASS` or `FAIL` strings. Threshold is finite from 0.0 through 1.0.

## Output Specification
Return `pass_rates` mapping batch IDs to rates rounded to three decimals and `below_threshold` as a set. A batch with zero checks has rate `None` and is below threshold.

## Rules and Constraints
- Count every check exactly once.
- Reject malformed data and duplicate IDs with `ValueError`.
- Do not mutate input.

## Hints
1. Keep pass and total counters per batch.
2. Handle zero total before division.
3. Compare the unrounded rate to the threshold, then report the rounded rate.

## Common Mistakes
- Comparing rounded rates to the threshold.
- Counting vehicles instead of checks.
- Treating an empty batch as perfect quality.

## Extension Challenge
Return the first failed component index for every vehicle in below-threshold batches.
