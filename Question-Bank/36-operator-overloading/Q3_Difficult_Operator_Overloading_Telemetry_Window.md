# 36_OperatorOverloading_TelemetryWindow

**Difficulty:** Difficult
**Primary Python Concept:** Operator overloading  
**Supporting Concepts:** Sequence protocol, slicing, iteration, immutability, type hints  
**Automotive Domain:** Offline telemetry window analysis  
**Estimated Completion Time:** 65 minutes

## Learning Objective
Implement a small sequence-like object with predictable indexing and concatenation.

## Prerequisites
Classes, special methods, lists, slicing, and exceptions.

## Scenario Introduction
A diagnostic tool groups a fixed window of sensor samples for repeatable offline analysis.

## Problem Statement
**Goal:** Implement a small sequence-like object with predictable indexing and concatenation.

**Specifically:** Implement `TelemetryWindow(values: tuple[float, ...])` with `__len__`, `__getitem__`, `__iter__`, `__add__`, and `average()`.

## Task to Implement
Indexing returns a float; slicing returns a new window; adding another window concatenates values. Average an empty window is invalid. Round average to two decimals.

## Input Specification
Values must be finite numbers. The constructor accepts a tuple and stores immutable data.

## Output Specification
Support integer indices, slices, iteration, concatenation, and numeric average.

## Rules and Constraints
- Do not expose a mutable internal list.
- Unrelated addition operands should return `NotImplemented`.
- Raise `ValueError` for empty averages or invalid values.

## Hints
Delegate indexing and slicing to the tuple, wrapping slices in a new object.

## Common Mistakes
- Returning a list for slices.
- Allowing mutable state changes.
- Dividing by zero for an empty window.

## Extension Challenge
Add a `delta()` method that returns adjacent differences.
