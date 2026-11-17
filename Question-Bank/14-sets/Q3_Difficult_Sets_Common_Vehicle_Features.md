# 14_Sets_CommonVehicleFeatures

**Difficulty:** Difficult  
**Primary Python Concept:** Set intersection across collections  
**Supporting Concepts:** Nested lists, normalization, validation, functions  
**Automotive Domain:** Simulated fleet feature analysis  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Find features common to every vehicle and features appearing in at least two vehicles.

## Prerequisites
Sets, nested collections, strings, loops, and validation.

## Scenario Introduction
An offline fleet catalog stores feature labels for each vehicle model.

## Problem Statement
**Goal:** Find features common to every vehicle and features appearing in at least two vehicles.

**Specifically:** Analyze shared and repeated features without allowing capitalization or whitespace to change identity.

## Task to Implement
Implement `analyze_common_features(vehicle_features: list[list[str]]) -> dict[str, object]`.

## Input Specification
There are 0 through 1,000 vehicles, each with 0 through 200 feature names. Names are non-empty strings of letters, digits, spaces, and hyphens.

## Output Specification
Return `common_to_all` as the intersection of all vehicle sets, `in_at_least_two` as the union of features whose vehicle count is at least two, and `vehicle_count`. Normalize feature names to title case after trimming repeated internal spaces.

## Rules and Constraints
- An empty fleet returns empty sets.
- A one-vehicle fleet has every feature in both result sets.
- Use sets for per-vehicle identity and counting.
- Reject malformed values with `ValueError`; do not mutate input.

## Hints
1. Normalize each vehicle into a set before analysis.
2. Start the all-vehicle intersection from the first set.
3. Count each feature at most once per vehicle.

## Common Mistakes
- Counting duplicate labels twice for one vehicle.
- Treating empty fleet intersection as a universal set.
- Using case-sensitive feature matching.

## Extension Challenge
Return the features present in exactly one vehicle as a third set.
