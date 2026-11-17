# 30_ClassMethodsAndStaticMethods_UnitConversion

**Difficulty:** Medium
**Primary Python Concept:** Class methods and static methods  
**Supporting Concepts:** Alternate constructors, conversion formulas, validation  
**Automotive Domain:** Offline measurement conversion utility  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Separate unit-independent conversion logic from class-level construction.

## Prerequisites
Classes, decorators, arithmetic, and exceptions.

## Scenario Introduction
A test report stores speed in km/h but accepts technician input in mph.

## Problem Statement
**Goal:** Separate unit-independent conversion logic from class-level construction.

**Specifically:** Create a converter object from mph and expose a static conversion helper.

## Task to Implement
Implement class `UnitConversion` with `from_mph(cls, mph: float) -> UnitConversion`, attribute `kmh`, and static method `mph_to_kmh(mph: float) -> float`.

## Input Specification
Mph is finite and from 0 through 250. Use exact factor `1.609344`.

## Output Specification
`mph_to_kmh` returns km/h rounded to three decimals. `from_mph` stores that rounded result in `kmh`.

## Rules and Constraints
- Use `@classmethod` for `from_mph` and `@staticmethod` for the formula.
- Raise `ValueError` outside the range.
- No locale-dependent formatting is required.

## Hints
1. Validate in the static method so both paths share it.
2. Multiply by `1.609344`.
3. Call the static method from the class method.

## Common Mistakes
- Using 1.6 and losing required precision.
- Requiring an instance to call the formula.
- Rounding the conversion factor itself.

## Extension Challenge
Add a class method for km/h input that uses a shared range validator.
