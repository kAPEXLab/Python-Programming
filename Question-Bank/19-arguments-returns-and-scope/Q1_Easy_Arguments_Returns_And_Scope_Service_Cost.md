---
layout: default
---

# 19_ArgumentsReturnsAndScope_ServiceCost

**Difficulty:** Easy  
**Primary Python Concept:** Arguments, return values, and local scope  
**Supporting Concepts:** Arithmetic, defaults, validation, rounding  
**Automotive Domain:** Offline service cost estimate  
**Estimated Completion Time:** 25 minutes

## Learning Objective
Use arguments and a local calculation to return a deterministic service estimate.

## Prerequisites
Function definitions, parameters, arithmetic, and exceptions.

## Scenario Introduction
A workshop simulation charges labor and parts for one service visit.

## Problem Statement
**Goal:** Use arguments and a local calculation to return a deterministic service estimate.

**Specifically:** Calculate subtotal, tax, and total without relying on global mutable state.

## Task to Implement
Implement `service_cost(labor_hours: float, hourly_rate: float, parts_cost: float, tax_rate: float = 0.08) -> dict[str, float]`.

## Input Specification
Hours are 0.0 through 100.0, rate and parts cost are 0.0 through 100000.0, and tax rate is 0.0 through 0.30. Values are finite non-booleans.

## Output Specification
Return `subtotal`, `tax`, and `total`, each rounded to two decimals. Tax is subtotal times tax rate.

## Rules and Constraints
- Keep intermediate values local to the function.
- Do not modify arguments or use globals.
- Raise `ValueError` for invalid values.

## Hints
1. Calculate labor before adding parts.
2. Compute tax from subtotal.
3. Round each reported field at the end.

## Common Mistakes
- Applying tax only to parts.
- Reusing a module-level accumulator.
- Rounding inputs before multiplication.

## Extension Challenge
Return a separate rounded labor subtotal and parts subtotal.
