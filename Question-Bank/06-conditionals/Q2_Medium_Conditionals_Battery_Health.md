---
layout: default
---

# 06_Conditionals_BatteryHealth

**Difficulty:** Medium  
**Primary Python Concept:** `if-else` and `if-elif-else` statements  
**Supporting Concepts:** Numeric ranges, validation, formatted messages  
**Automotive Domain:** Electric-vehicle battery health  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Use ordered conditional branches to classify battery state of charge (SOC), the percentage of usable energy remaining.

## Prerequisites
Functions, numeric comparisons, ranges, and formatted strings.

## Scenario Introduction
Battery SOC is expressed as a percentage from 0% to 100%. A simulated dashboard labels SOC below 20% as `LOW`, 20% through 80% as `OK`, and above 80% as `HIGH`.

## Problem Statement
**Goal:** Use ordered conditional branches to classify battery state of charge (SOC), the percentage of usable energy remaining.

**Specifically:** Return a message containing the SOC and its classification.

## Task to Implement
Implement `classify_battery_soc(soc_percent: float) -> str`.

## Input Specification
SOC must be from 0 through 100 percent inclusive. Reject other values with `ValueError`.

## Output Specification
Return `SOC: X.0% - STATUS`, displaying one decimal place.

## Rules and Constraints
- Use `if-elif-else`.
- Use boundaries exactly as stated.
- Do not round before classification.

## Hints
1. Validate first.
2. Test the lowest interval before the middle interval.
3. Format only the displayed percentage.

## Common Mistakes
- Classifying 20% as low.
- Classifying 80% as high.
- Rounding before comparing.

## Extension Challenge
Add a `CRITICAL` state for SOC below 5%.
