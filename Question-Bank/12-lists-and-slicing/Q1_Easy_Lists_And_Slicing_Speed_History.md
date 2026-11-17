---
layout: default
---

# 12_ListsAndSlicing_SpeedHistory

**Difficulty:** Easy  
**Primary Python Concept:** Lists and basic slicing  
**Supporting Concepts:** Indexing, validation, arithmetic, functions  
**Automotive Domain:** Simulated vehicle speed history  
**Estimated Completion Time:** 25 minutes

## Learning Objective
Use list indexing and slices to inspect a recent portion of an ordered speed history.

## Prerequisites
Variables, numbers, lists, functions, and conditionals.

## Scenario Introduction
An offline driving simulation stores speed readings in kilometers per hour from oldest to newest.

## Problem Statement
**Goal:** Use list indexing and slices to inspect a recent portion of an ordered speed history.

**Specifically:** Return the first reading, last reading, and the most recent three readings.

## Task to Implement
Implement `summarize_speed_history(readings: list[int]) -> dict[str, object]`.

## Input Specification
`readings` must contain 3 through 100 integer speeds from 0 through 240 km/h. Boolean values are invalid.

## Output Specification
Return `first`, `last`, and `recent_three`, preserving integer values and input order.

## Rules and Constraints
- Use indexing for the first and last readings.
- Use a slice for `recent_three`.
- Raise `ValueError` for invalid input.
- Do not mutate the list.

## Hints
1. Validate every item before indexing.
2. The last item has index `-1`.
3. The slice `[-3:]` selects the recent readings.

## Common Mistakes
- Sorting the readings before returning them.
- Returning a tuple instead of a list for the slice.
- Accepting out-of-range speeds.

## Extension Challenge
Also return the average of the recent three readings rounded to one decimal place.
