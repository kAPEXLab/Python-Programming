---
layout: default
---

# 28_ClassesAndObjects_BatteryPack

**Difficulty:** Medium
**Primary Python Concept:** Classes and objects  
**Supporting Concepts:** State, calculations, validation  
**Automotive Domain:** Offline battery-pack model  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Represent battery state as an object and expose a calculated energy value.

## Prerequisites
Classes, floats, methods, and exceptions.

## Scenario Introduction
A simulator tracks nominal battery capacity and state of charge for one pack.

## Problem Statement
**Goal:** Represent battery state as an object and expose a calculated energy value.

**Specifically:** Create a battery object that calculates currently stored energy.

## Task to Implement
Implement class `BatteryPack` with `capacity_kwh: float`, `soc_percent: float`, and method `stored_energy_kwh(self) -> float`.

## Input Specification
Capacity is greater than 0 and at most 500 kWh. SOC is from 0 through 100 inclusive. Values must be finite numbers.

## Output Specification
Return capacity times SOC divided by 100, rounded to two decimals.

## Rules and Constraints
- Store the two values on each instance.
- Raise `ValueError` for invalid construction.
- This is a static model, not a battery-management interface.

## Hints
1. Validate ranges in the constructor.
2. Keep SOC as a percentage, not a fraction.
3. Round the method result only at return time.

## Common Mistakes
- Dividing SOC by 10 instead of 100.
- Allowing negative capacity.
- Making capacity a shared class attribute.

## Extension Challenge
Add a method for usable energy after a fixed 5% reserve.
