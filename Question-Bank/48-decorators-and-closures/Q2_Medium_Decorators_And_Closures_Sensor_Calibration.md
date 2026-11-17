---
layout: default
---

# 48_DecoratorsAndClosures_SensorCalibration

**Difficulty:** Medium  
**Primary Python Concept:** Parameterized decorators and closures  
**Supporting Concepts:** Factory functions, numeric transformation, metadata  
**Automotive Domain:** Offline sensor calibration  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Create a configurable decorator that applies a fixed calibration offset.

## Prerequisites
Decorators, closures, functions, numeric types, and validation.

## Scenario Introduction
A test harness calibrates prerecorded sensor readings before a check consumes them.

## Problem Statement
**Goal:** Create a configurable decorator that applies a fixed calibration offset.

**Specifically:** Implement `calibrated(offset: float) -> Callable` for functions accepting one numeric reading.

## Task to Implement
The decorated function must receive `reading + offset`, return its result, reject a non-finite offset at decoration time, and reject non-finite readings when the wrapper is called.

## Input Specification
Offset and readings are finite numbers; booleans are not valid numeric readings or offsets.

## Output Specification
Return exactly the wrapped function's result after calibration.

## Rules and Constraints
- Store offset in a closure.
- Preserve wrapped metadata.
- Never mutate caller-owned collections.

## Hints
The outer function validates and captures offset; the inner wrapper adjusts the argument.

## Common Mistakes
- Applying the offset after the wrapped function runs.
- Reusing one mutable offset across decorators.
- Accepting `nan`.

## Extension Challenge
Support separate scale and offset parameters.
