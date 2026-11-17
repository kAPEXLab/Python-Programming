# 20_VariadicArgumentsLambdaAndHigherOrderFunctions_FleetMetrics

**Difficulty:** Difficult  
**Primary Python Concept:** Variadic arguments and function composition  
**Supporting Concepts:** Higher-order functions, lambdas, reducers, validation  
**Automotive Domain:** Simulated fleet metrics pipeline  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Compose a variable number of metric functions and apply them to validated fleet values.

## Prerequisites
Functions, `*args`, lambdas, callable values, lists, and exceptions.

## Scenario Introduction
An offline fleet tool receives numeric distances and lets callers choose metric functions.

## Problem Statement
**Goal:** Compose a variable number of metric functions and apply them to validated fleet values.

**Specifically:** Apply each supplied metric function to the same readings and return results by function name.

## Task to Implement
Implement `apply_fleet_metrics(readings: list[float], *metrics: tuple[str, typing.Callable[[list[float]], float]]) -> dict[str, float]`.

## Input Specification
Readings are 0 through 1000 finite kilometers, with at least one item. Each metric is `(name, function)`, names are unique non-empty strings, and functions accept `list[float]` and return finite numbers. Non-numeric or non-finite readings and metric results raise `ValueError`.

## Output Specification
Call each metric in input order and return a dictionary mapping names to results rounded to two decimals. A metric exception must propagate unchanged.

## Rules and Constraints
- Use higher-order calls; do not identify functions by name with conditionals.
- Do not mutate readings or metric tuples.
- Reject malformed inputs with `ValueError`.

## Hints
1. Validate callable objects with `callable()`.
2. Store each returned metric under its supplied name.
3. Round only after the callable returns.

## Common Mistakes
- Calling every function with one reading instead of the full list.
- Silently swallowing callable exceptions.
- Overwriting duplicate metric names.

## Extension Challenge
Accept a callable that receives the prior result and the next metric result to build a pipeline summary.
