---
layout: default
---

# 31_EncapsulationAndProperties_Odometer

**Difficulty:** Difficult
**Primary Python Concept:** Encapsulation and properties  
**Supporting Concepts:** Monotonic state, setters, invariants  
**Automotive Domain:** Offline odometer model  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Enforce a non-decreasing odometer through an encapsulated property.

## Prerequisites
Classes, properties, comparisons, and exceptions.

## Scenario Introduction
A simulator receives periodic odometer updates and must reject rollback values.

## Problem Statement
**Goal:** Enforce a non-decreasing odometer through an encapsulated property.

**Specifically:** Create an odometer object whose reading can only increase or remain equal.

## Task to Implement
Implement class `Odometer` with property `kilometers: float` and method `add_distance(self, distance_km: float) -> float`.

## Input Specification
Initial kilometers are 0 through 2,000,000. Added distance is from 0 through 5000 km. Values must be finite numbers, excluding booleans.

## Output Specification
The property and method return kilometers rounded to one decimal. `add_distance` increases the reading by the supplied distance.

## Rules and Constraints
- Store the backing value privately as `_kilometers`.
- Direct assignment may not reduce the reading; raise `ValueError` if it does.
- Do not connect to a real odometer.

## Hints
1. Validate the candidate assignment against the current value.
2. Let `add_distance` use the property setter or shared validation.
3. Permit equal assignments.

## Common Mistakes
- Allowing rollback values.
- Rejecting a zero-distance update.
- Rounding before comparing values.

## Extension Challenge
Track the number of accepted updates with a read-only property.
