---
layout: default
---

# 29_ConstructorsAttributesAndInstanceMethods_ChargingSession

**Difficulty:** Medium
**Primary Python Concept:** Constructors, attributes, and instance methods  
**Supporting Concepts:** State changes, percentages, guards  
**Automotive Domain:** Offline charging-session state  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Use instance methods to update a validated charging-session object safely.

## Prerequisites
Classes, attributes, methods, conditionals, and exceptions.

## Scenario Introduction
A simulator tracks a session's initial SOC and current SOC as charging energy is applied.

## Problem Statement
**Goal:** Use instance methods to update a validated charging-session object safely.

**Specifically:** Create a session and increase its SOC without exceeding 100%.

## Task to Implement
Implement class `ChargingSession` with `__init__(self, initial_soc: float)` and `add_soc(self, increase: float) -> float`.

## Input Specification
Initial SOC is 0 through 100. Each increase is positive and at most 100 percentage points.

## Output Specification
`add_soc` updates the instance and returns the new SOC rounded to one decimal. Reject an increase that would exceed 100.

## Rules and Constraints
- Store current SOC as an instance attribute.
- Raise `ValueError` for invalid construction or updates.
- This object simulates state only.

## Hints
1. Validate the proposed new value before assignment.
2. Keep current SOC separate from the initial value.
3. Return the updated attribute.

## Common Mistakes
- Silently clamping overcharge to 100.
- Updating before validating.
- Using a class-level SOC.

## Extension Challenge
Add a `finish()` method that rejects sessions below a minimum target SOC.
