# 21_Recursion_ChargingPlan

**Difficulty:** Difficult  
**Primary Python Concept:** Recursive backtracking  
**Supporting Concepts:** Tuples, constraints, search, validation, deterministic choice  
**Automotive Domain:** Simulated charging plan selection  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Use recursion and backtracking to select charging sessions that reach a target energy with minimum session count.

## Prerequisites
Recursion, lists, tuples, arithmetic, sorting, and validation.

## Scenario Introduction
An offline planner has fixed charging session options measured in kWh. Each option can be used at most once.

## Problem Statement
**Goal:** Use recursion and backtracking to select charging sessions that reach a target energy with minimum session count.

**Specifically:** Find an exact combination of sessions that reaches the target energy using the fewest sessions.

## Task to Implement
Implement `plan_charging(target_kwh: int, sessions: list[int]) -> tuple[int, ...] | None`.

## Input Specification
Target is an integer from 0 through 500. Sessions contain 0 through 30 unique positive integers from 1 through 500. Every value is measured in whole kWh.

## Output Specification
Return a tuple of selected session values whose sum equals target and whose length is minimal. Return `None` when no exact combination exists. For ties, return the lexicographically smallest sorted tuple. Target zero returns `()`.

## Rules and Constraints
- Use recursive backtracking; each session can be selected once.
- Do not mutate the input list.
- Validate all values and keep results deterministic.

## Hints
1. Define a recursive search with a start index and remaining target.
2. Track the best valid combination rather than stopping at the first one.
3. Sort candidate tuples before applying the tie-break rule.

## Common Mistakes
- Reusing a session more than once.
- Returning a non-minimal combination.
- Treating an impossible target as an exception.

## Extension Challenge
Add a maximum available charging time per session and optimize total time after session count.
