# 30_ClassMethodsAndStaticMethods_FaultCatalog

**Difficulty:** Difficult
**Primary Python Concept:** Class methods and static methods  
**Supporting Concepts:** Class state, lookup, immutable-style construction  
**Automotive Domain:** Offline diagnostic fault catalog  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Use class-level catalog data with a class method constructor and a static code validator.

## Prerequisites
Classes, dictionaries, class methods, static methods, and strings.

## Scenario Introduction
A simulator maintains a small catalog of known fault descriptions.

## Problem Statement
**Goal:** Use class-level catalog data with a class method constructor and a static code validator.

**Specifically:** Create catalog objects from codes while validating code syntax independently.

## Task to Implement
Implement class `FaultCatalog` with class attribute `DESCRIPTIONS`, class method `from_code(cls, code: str) -> FaultCatalog`, and static method `valid_code(code: str) -> bool`. Store normalized `code` and `description`.

## Input Specification
Codes are 2 to 8 uppercase letters, digits, or hyphens. `DESCRIPTIONS` contains `P0420: "Catalyst efficiency low"` and `BMS-01: "Cell imbalance"`.

## Output Specification
Known codes use their description; unknown valid codes use `Unknown fault`. Invalid codes raise `ValueError`.

## Rules and Constraints
- `valid_code` returns only a boolean.
- `from_code` must use `cls` and uppercase normalization.
- Do not modify `DESCRIPTIONS`.

## Hints
1. Validate before uppercasing or after consistently normalizing.
2. Use `cls.DESCRIPTIONS.get`.
3. Keep syntax validation independent of catalog membership.

## Common Mistakes
- Returning false for every unknown code.
- Mutating the shared catalog during lookup.
- Making the validator an instance method.

## Extension Challenge
Add a class method that returns a sorted list of all known codes.
