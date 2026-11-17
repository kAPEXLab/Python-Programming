---
layout: default
---

# 05_Operators_FuelEconomy

**Difficulty:** Easy  
**Primary Python Concept:** Operators and expressions  
**Supporting Concepts:** Numeric types, conversion, rounding  
**Automotive Domain:** Fuel-efficiency analysis  
**Estimated Completion Time:** 20 minutes

## Learning Objective
Use arithmetic operators to calculate fuel economy accurately.

## Prerequisites
Variables, functions, numeric values, and formatted output.

## Scenario Introduction
Fuel economy describes fuel used for a distance. This exercise reports liters per 100 km from a trip's fuel and distance.

## Problem Statement
**Goal:** Use arithmetic operators to calculate fuel economy accurately.

**Specifically:** Calculate fuel economy using the formula `fuel_liters / distance_km * 100`.

## Task to Implement
Implement `fuel_economy(fuel_liters: float, distance_km: float) -> float`.

## Input Specification
Fuel is 0 through 500 liters; distance is 0.1 through 5,000 km. Reject invalid values with `ValueError`.

## Output Specification
Return a float rounded to two decimal places in liters per 100 km. Zero fuel returns `0.0`.

## Rules and Constraints
- Follow the formula exactly.
- Do not divide by zero.
- Do not print from the function.

## Hints
1. Validate distance before division.
2. Apply multiplication by 100 after division.
3. Round only the result.

## Common Mistakes
- Reversing fuel and distance.
- Using integer division.
- Treating zero fuel as invalid.

## Extension Challenge
Return both liters per 100 km and kilometers per liter.
