---
layout: default
---

# 11_NestedLoops_InspectionSearch

**Difficulty:** Difficult  
**Primary Python Concept:** Nested loops with loop `else`  
**Supporting Concepts:** Searching, validation, early exit, dictionaries  
**Automotive Domain:** Manufacturing inspection search  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Search a multi-level inspection report and distinguish found, not-found, and invalid outcomes using nested loops and loop `else`.

## Prerequisites
Nested loops, loop `else`, dictionaries, strings, validation, and exceptions.

## Scenario Introduction
A manufacturing report groups inspection records by vehicle. Each record has a component and status. Engineers need to find the first vehicle containing a specified failed component.

## Problem Statement
**Goal:** Search a multi-level inspection report and distinguish found, not-found, and invalid outcomes using nested loops and loop `else`.

**Specifically:** Search vehicles in input order and components in each vehicle's input order.

## Task to Implement
Implement `find_first_failed_component(report: list[dict[str, object]], component_name: str) -> str | None`. Each vehicle dictionary has `vehicle_id` and `checks`, where checks is a list of `{component, status}` dictionaries. Return the first vehicle ID where the requested component has status `FAIL`.

## Input Specification
- Up to 10,000 vehicles and 100 checks per vehicle.
- IDs and component names are non-empty strings.
- Status is `PASS` or `FAIL`, case-insensitive.
- Component search is case-insensitive after trimming.
- Reject malformed records with `ValueError`.

## Output Specification
Return the first matching vehicle ID, or `None` after a complete search. A component with `PASS` does not match.

## Rules and Constraints
- Use nested loops.
- Use loop `else` on at least the inner or outer search loop to represent no match.
- Stop after the first matching vehicle.
- Do not mutate input.

## Hints
1. Normalize the requested component once.
2. Track whether the inner search found a failed matching check.
3. Use `break` to stop both searches at the first vehicle match.

## Common Mistakes
- Returning a vehicle for a matching component that passed.
- Continuing after a match.
- Forgetting to validate nested checks.
- Misusing loop `else` so it runs after a successful `break`.

## Extension Challenge
Return the vehicle ID and component-check index as a tuple.
