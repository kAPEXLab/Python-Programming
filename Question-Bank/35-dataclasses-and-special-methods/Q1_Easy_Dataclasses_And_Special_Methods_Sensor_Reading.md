---
layout: default
---

# 35_DataclassesAndSpecialMethods_SensorReading

**Difficulty:** Easy
**Primary Python Concept:** Dataclasses and special methods  
**Supporting Concepts:** Frozen records, validation, ordering, representation  
**Automotive Domain:** Offline sensor reading records  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Use a dataclass to model immutable, comparable sensor readings.

## Prerequisites
Classes, dataclasses, tuples, validation, and sorting.

## Scenario Introduction
A test harness stores normalized sensor readings that must be safe to compare and reuse.

## Problem Statement
**Goal:** Use a dataclass to model immutable, comparable sensor readings.

**Specifically:** Define frozen dataclass `SensorReading` with fields `sensor: str`, `value: float`, and `unit: str`. Implement `average_reading(readings: list[SensorReading]) -> SensorReading`.

## Task to Implement
Validate non-empty sensor and unit names and finite values. Average readings only when all sensor and unit fields match; return a new reading rounded to two decimals.

## Input Specification
The list must be non-empty. All readings must use the same sensor and unit.

## Output Specification
Return the average record with the shared sensor and unit.

## Rules and Constraints
- Make the dataclass immutable.
- Equality must compare all fields through dataclass behavior.
- Raise `ValueError` for incompatible or invalid input.

## Hints
Use `@dataclass(frozen=True)` and validate in `__post_init__`.

## Common Mistakes
- Mutating a frozen instance.
- Averaging records with different units.
- Returning a mutable dictionary.

## Extension Challenge
Add ordering by timestamp with a second dataclass field.
