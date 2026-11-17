---
layout: default
---

# 25_DataValidation_ChargingRequest

**Difficulty:** Medium
**Primary Python Concept:** Data validation  
**Supporting Concepts:** Cross-field rules, literals, numeric constraints  
**Automotive Domain:** Offline charging request validation  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Apply both field-level and cross-field validation to a charging request.

## Prerequisites
Dictionaries, conditionals, type checks, and exceptions.

## Scenario Introduction
A charging planner receives a requested current, target state of charge, and connector type.

## Problem Statement
**Goal:** Apply both field-level and cross-field validation to a charging request.

**Specifically:** Normalize a request only if its values are safe for the simulated connector.

## Task to Implement
Implement `validate_charging_request(request: dict[str, object]) -> dict[str, object]`.

## Input Specification
Keys are `connector` (`AC` or `DC`), `current_a` (1-500), and `target_soc` (1-100). DC current may be up to 500 A; AC current may be up to 80 A. Values are finite numbers where applicable.

## Output Specification
Return `{"connector": uppercase, "current_a": float, "target_soc": float}`. Raise `ValueError` for invalid keys, types, ranges, or connector limits.

## Rules and Constraints
- Reject extra keys.
- Target SOC must be greater than 0 and at most 100.
- This is a planning validation function, not a charger controller.

## Hints
1. Normalize the connector before cross-field checks.
2. Use a connector-to-limit mapping.
3. Validate the key set before reading values.

## Common Mistakes
- Applying the same current limit to AC and DC.
- Allowing target SOC above 100.
- Returning the caller's mutable dictionary.

## Extension Challenge
Add battery chemistry with separate maximum SOC values.
