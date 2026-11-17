# 38_RaisingAndCustomExceptions_BatterySafetyLimit

**Difficulty:** Easy
**Primary Python Concept:** Raising and defining custom exceptions  
**Supporting Concepts:** Exception hierarchy, validation, type hints, numeric rules  
**Automotive Domain:** Offline battery safety validation  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Define and raise a domain-specific exception when a simulated battery request exceeds a safety limit.

## Prerequisites
Classes, functions, exceptions, and numeric validation.

## Scenario Introduction
A charging simulator must reject unsafe current requests before producing a plan.

## Problem Statement
**Goal:** Define and raise a domain-specific exception when a simulated battery request exceeds a safety limit.

**Specifically:** Define `BatterySafetyLimit(Exception)` and implement `validate_charge_request(soc_percent: float, current_a: float) -> str`.

## Task to Implement
Return `ACCEPTED` when state of charge is 0 through 100 and current is 0 through 32 inclusive. Raise `BatterySafetyLimit` when current exceeds 32; raise `ValueError` for invalid SOC or negative current.

## Input Specification
Both inputs must be finite numbers. SOC is expected from 0 through 100.

## Output Specification
Return exactly `ACCEPTED` for valid requests.

## Rules and Constraints
- The custom exception must carry the requested current and limit.
- Do not clamp unsafe current.
- This function never controls a charger.

## Hints
Validate generic numeric constraints before raising the domain-specific exception.

## Common Mistakes
- Using `ValueError` for every failure.
- Silently reducing current.
- Accepting SOC above 100.

## Extension Challenge
Add a temperature input with a separate custom exception.
