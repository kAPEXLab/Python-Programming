---
layout: default
---

# 48_DecoratorsAndClosures_TimingDiagnostics

**Difficulty:** Easy  
**Primary Python Concept:** Function decorators  
**Supporting Concepts:** Closures, `functools.wraps`, return values  
**Automotive Domain:** Offline diagnostic timing  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Wrap a diagnostic function while preserving its metadata and result.

## Prerequisites
Functions, nested functions, decorators, and `time.perf_counter`.

## Scenario Introduction
A local diagnostic harness records elapsed time around a simulated check.

## Problem Statement
**Goal:** Wrap a diagnostic function while preserving its metadata and result.

**Specifically:** Implement `timed_check(func: Callable[..., T]) -> Callable[..., tuple[T, float]]`.

## Task to Implement
Return a decorated function that returns `(original_result, elapsed_seconds)` and preserves `__name__` and `__doc__`.

## Input Specification
The wrapped callable accepts arbitrary positional and keyword arguments.

## Output Specification
Elapsed time is a non-negative float from the supplied clock.

## Rules and Constraints
- Use a closure and `functools.wraps`.
- Do not alter the original result.
- Timing is local simulation only.

## Hints
Capture the clock before and after calling the function, then subtract.

## Common Mistakes
- Swallowing wrapped exceptions.
- Returning only elapsed time.
- Omitting `functools.wraps`.

## Extension Challenge
Add a logger callback that receives the function name and elapsed time.
