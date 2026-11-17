# 36_OperatorOverloading_Distance

**Difficulty:** Easy
**Primary Python Concept:** Operator overloading  
**Supporting Concepts:** Immutable value objects, comparisons, numeric validation, formatting  
**Automotive Domain:** Offline trip distance arithmetic  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Implement safe arithmetic and comparisons for a distance value object.

## Prerequisites
Classes, special methods, numeric operators, and exceptions.

## Scenario Introduction
A trip simulator needs distances that cannot be accidentally combined with unrelated units.

## Problem Statement
**Goal:** Implement safe arithmetic and comparisons for a distance value object.

**Specifically:** Implement `Distance(km: float)` with `__add__`, `__sub__`, `__lt__`, `__eq__`, and `__str__`.

## Task to Implement
Distance arithmetic must return new `Distance` objects. Subtraction may not produce a negative result. String output is `NN.N km` with one decimal place.

## Input Specification
Kilometers must be finite and non-negative. Arithmetic operands must also be `Distance` objects.

## Output Specification
Return value objects for arithmetic, booleans for comparisons, and formatted text for `str`.

## Rules and Constraints
- Do not mutate either operand.
- Return `NotImplemented` for unrelated operand types.
- Raise `ValueError` for negative results or invalid construction.

## Hints
Validate in the constructor and delegate operand validation in each operator.

## Common Mistakes
- Mutating the left operand.
- Comparing raw numbers silently.
- Rounding stored values instead of display values.

## Extension Challenge
Add multiplication by a non-negative numeric route count.
