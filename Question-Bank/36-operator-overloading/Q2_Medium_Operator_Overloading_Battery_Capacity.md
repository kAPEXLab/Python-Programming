# 36_OperatorOverloading_BatteryCapacity

**Difficulty:** Medium
**Primary Python Concept:** Operator overloading  
**Supporting Concepts:** Value objects, reflected operators, clamping, type checks  
**Automotive Domain:** Offline battery capacity accounting  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Overload arithmetic for a capacity type while enforcing physical bounds.

## Prerequisites
Classes, special methods, arithmetic, and validation.

## Scenario Introduction
A simulator models charge added to or consumed from a battery pack.

## Problem Statement
**Goal:** Overload arithmetic for a capacity type while enforcing physical bounds.

**Specifically:** Implement `BatteryCapacity(kwh: float, maximum_kwh: float)` with `__add__`, `__sub__`, `__rsub__`, and `percent()`.

## Task to Implement
The maximum must be positive and current capacity must be from 0 through maximum. Addition and subtraction use another `BatteryCapacity` with the same maximum and reject results outside bounds. `percent()` returns a percentage rounded to one decimal.

## Input Specification
All capacities are finite. Maximum capacity is 1 through 2000 kWh.

## Output Specification
Arithmetic returns a new capacity with the same maximum; percent returns a float.

## Rules and Constraints
- Preserve the maximum in results.
- Reject mismatched maximum capacities with `ValueError`.
- Do not connect to a real battery.

## Hints
Check maximum capacities before calculating the new current value.

## Common Mistakes
- Clamping silently instead of rejecting invalid arithmetic.
- Comparing only current capacity.
- Returning a raw float from addition.

## Extension Challenge
Implement `__repr__` with an exact constructor-like format.
