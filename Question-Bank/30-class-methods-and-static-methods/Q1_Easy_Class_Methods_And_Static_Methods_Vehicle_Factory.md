---
layout: default
---

# 30_ClassMethodsAndStaticMethods_VehicleFactory

**Difficulty:** Easy
**Primary Python Concept:** Class methods and static methods  
**Supporting Concepts:** Alternate constructors, validation, class state  
**Automotive Domain:** Offline vehicle object factory  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Use a class method as an alternate constructor and a static method for shared validation.

## Prerequisites
Classes, constructors, class methods, static methods, and exceptions.

## Scenario Introduction
A simulator creates vehicles from compact specification text such as `EV-1|sedan|2026`.

## Problem Statement
**Goal:** Use a class method as an alternate constructor and a static method for shared validation.

**Specifically:** Parse the specification and construct a validated vehicle object.

## Task to Implement
Implement class `VehicleFactory` with `from_spec(cls, spec: str) -> VehicleFactory` and static method `valid_year(year: int) -> bool`. Store `vehicle_id`, `kind`, and `year`.

## Input Specification
Spec has exactly three pipe-separated fields. ID is non-empty, kind is `sedan`, `suv`, or `truck`, and year is 2000 through 2100.

## Output Specification
`valid_year` returns a boolean. `from_spec` returns an instance with uppercase ID and lowercase kind.

## Rules and Constraints
- `from_spec` must call class construction through `cls`.
- Raise `ValueError` for malformed specifications.
- No registry or external factory service is used.

## Hints
1. Split and validate the field count.
2. Convert year only after checking text shape.
3. Use `@classmethod` and `@staticmethod` decorators.

## Common Mistakes
- Calling `VehicleFactory(...)` instead of `cls(...)`.
- Making `valid_year` depend on instance state.
- Accepting unknown vehicle kinds.

## Extension Challenge
Add a class counter for successfully created vehicles.
