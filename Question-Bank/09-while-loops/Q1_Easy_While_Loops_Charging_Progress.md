# 09_WhileLoops_ChargingProgress

**Difficulty:** Easy  
**Primary Python Concept:** `while` loops  
**Supporting Concepts:** Arithmetic, validation, termination conditions  
**Automotive Domain:** Simulated EV charging  
**Estimated Completion Time:** 25 minutes

## Learning Objective
Use a `while` loop to advance a charging percentage until a target is reached.

## Prerequisites
Variables, arithmetic, functions, conditionals, and loops.

## Scenario Introduction
A charging station simulation increases battery state of charge (SOC) in fixed percentage steps. No real charger or vehicle is used.

## Problem Statement
**Goal:** Use a `while` loop to advance a charging percentage until a target is reached.

**Specifically:** Calculate how many charging steps are required to reach a target SOC.

## Task to Implement
Implement `charging_steps(start_soc: int, target_soc: int, step_percent: int) -> int`.

## Input Specification
SOC values are integers from 0 through 100, with start at most target. Step is 1 through 100.

## Output Specification
Return the number of steps, including a final partial step if the increment would pass the target. If start equals target, return 0.

## Rules and Constraints
- Use a `while` loop.
- Never return a negative count.
- Raise `ValueError` for invalid input.

## Hints
1. Keep a current SOC and step counter.
2. Continue while current SOC is below target.
3. Cap the final SOC at the target.

## Common Mistakes
- Creating an infinite loop.
- Counting the initial state as a step.
- Rejecting a partial final increment.

## Extension Challenge
Return the SOC after every step as a list.
