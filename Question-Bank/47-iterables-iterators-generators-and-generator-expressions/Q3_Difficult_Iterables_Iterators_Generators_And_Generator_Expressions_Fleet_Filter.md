# 47_IterablesIteratorsGeneratorsAndGeneratorExpressions_FleetFilter

**Difficulty:** Difficult  
**Primary Python Concept:** Generator expressions and composable iterables  
**Supporting Concepts:** `filter`, `map`, predicates, laziness  
**Automotive Domain:** Offline fleet filtering  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Compose lazy transformations to select fleet records by battery state and distance.

## Prerequisites
Generator expressions, dictionaries, iterables, predicates, and numeric validation.

## Scenario Introduction
A fleet analyst wants qualifying prerecorded trips without creating unnecessary intermediate lists.

## Problem Statement
**Goal:** Compose lazy transformations to select fleet records by battery state and distance.

**Specifically:** Implement `qualifying_trips(records: Iterable[dict[str, object]], minimum_soc: int) -> Iterator[str]`.

## Task to Implement
Yield each `vehicle_id` whose integer `soc` is at least `minimum_soc` and whose `distance_km` exceeds 10.0, in input order.

## Input Specification
Records contain non-empty string `vehicle_id`, integer `soc` 0 through 100, and non-negative numeric `distance_km`. `minimum_soc` must be an integer from 0 through 100.

## Output Specification
Yield matching vehicle IDs lazily; malformed records raise `ValueError` when reached.

## Rules and Constraints
- Use a generator expression or generator pipeline.
- Do not sort or materialize the input.
- All data is offline.

## Hints
Validate each record inside the generator so evaluation remains lazy.

## Common Mistakes
- Building a list before returning.
- Using `>=` for the distance condition.
- Validating records that the consumer never reaches.

## Extension Challenge
Accept a predicate callback for custom fleet policies.
