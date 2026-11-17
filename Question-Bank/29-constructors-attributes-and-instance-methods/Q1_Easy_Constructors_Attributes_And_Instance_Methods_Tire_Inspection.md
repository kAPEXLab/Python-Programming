# 29_ConstructorsAttributesAndInstanceMethods_TireInspection

**Difficulty:** Easy
**Primary Python Concept:** Constructors, attributes, and instance methods  
**Supporting Concepts:** Lists, thresholds, formatted status  
**Automotive Domain:** Offline tire inspection  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Design a class whose constructor validates measurements and whose method derives status.

## Prerequisites
Classes, constructors, lists, conditionals, and validation.

## Scenario Introduction
An inspector records tread depth for four tires in millimeters.

## Problem Statement
**Goal:** Design a class whose constructor validates measurements and whose method derives status.

**Specifically:** Create a tire inspection object and classify the set as `PASS` or `REPLACE`.

## Task to Implement
Implement class `TireInspection` with constructor `__init__(self, depths_mm: list[float])` and method `status(self) -> str`.

## Input Specification
Exactly four finite depths are required, each from 0 through 20 mm.

## Output Specification
Return `REPLACE` if any depth is below 1.6 mm; otherwise return `PASS`.

## Rules and Constraints
- Copy the input list so outside mutation cannot alter the object.
- Raise `ValueError` for wrong length or invalid values.
- The threshold is strictly below 1.6.

## Hints
1. Validate length before iterating values.
2. Store `list(depths_mm)`.
3. Use `any` for the replacement rule.

## Common Mistakes
- Accepting three or five tires.
- Using `<= 1.6` instead of `< 1.6`.
- Keeping the caller's list by reference.

## Extension Challenge
Report the index of every tire below the threshold.
