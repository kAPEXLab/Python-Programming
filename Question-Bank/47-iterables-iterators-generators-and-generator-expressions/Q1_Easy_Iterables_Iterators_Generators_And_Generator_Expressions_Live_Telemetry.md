# 47_IterablesIteratorsGeneratorsAndGeneratorExpressions_LiveTelemetry

**Difficulty:** Easy  
**Primary Python Concept:** Iterables and iterators  
**Supporting Concepts:** `iter`, `next`, protocols, sentinels  
**Automotive Domain:** Offline live-telemetry replay  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Consume a finite telemetry iterable one sample at a time without indexing assumptions.

## Prerequisites
Lists, tuples, loops, functions, and exceptions.

## Scenario Introduction
A replay tool presents prerecorded speed samples through the iterator protocol.

## Problem Statement
**Goal:** Consume a finite telemetry iterable one sample at a time without indexing assumptions.

**Specifically:** Implement `first_valid_speed(samples: Iterable[float]) -> float`.

## Task to Implement
Return the first finite speed from 0 through 300 km/h, consuming samples in order. Raise `ValueError` if none qualifies.

## Input Specification
Any iterable of numeric values; invalid values are skipped.

## Output Specification
Return the first valid speed unchanged.

## Rules and Constraints
- Do not require a list or use indexing.
- Consume lazily until a result is found.
- Replay data is offline.

## Hints
Use a `for` loop over the iterable and validate each value before returning.

## Common Mistakes
- Calling `len` on every iterable.
- Materializing an infinite source.
- Treating `None` as zero.

## Extension Challenge
Return the sample index alongside the speed without indexing the source.
