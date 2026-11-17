---
layout: default
---

# 37_BuiltInExceptionsAndTryExcept_MissingVehicleField

**Difficulty:** Medium
**Primary Python Concept:** Built-in exceptions and try-except  
**Supporting Concepts:** Dictionaries, `KeyError`, `TypeError`, defaults, validation  
**Automotive Domain:** Offline vehicle record lookup  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Use targeted exception handling when reading optional and required vehicle fields.

## Prerequisites
Dictionaries, functions, `try-except`, and basic type checks.

## Scenario Introduction
A report generator reads partial vehicle dictionaries from a simulated archive.

## Problem Statement
**Goal:** Use targeted exception handling when reading optional and required vehicle fields.

**Specifically:** Implement `vehicle_label(record: dict[str, object]) -> str`. Read required `vehicle_id` and optional `model_year`, defaulting a missing year to `"unknown"`.

## Task to Implement
Return `vehicle_id (year)` as text. Missing required ID raises `KeyError`; invalid ID or year types raise `TypeError`.

## Input Specification
IDs are non-empty strings. A supplied model year is an integer from 1886 through 2100.

## Output Specification
Return exact format such as `EV-1 (2026)` or `EV-1 (unknown)`.

## Rules and Constraints
- Handle only the optional field's `KeyError` as a default.
- Do not catch and suppress missing required fields.
- Records are offline dictionaries.

## Hints
Use a narrow `try` block around only the optional dictionary lookup.

## Common Mistakes
- Returning an empty ID.
- Catching `Exception` broadly.
- Treating string years as integers.

## Extension Challenge
Add optional `trim` text with a separate default.
