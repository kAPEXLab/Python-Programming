# 18_FunctionDefinitionAndParameters_DiagnosticFormatter

**Difficulty:** Difficult  
**Primary Python Concept:** Function definitions with keyword-only parameters  
**Supporting Concepts:** Strings, validation, formatting, defaults  
**Automotive Domain:** Offline diagnostic message formatting  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Define a formatting function with a keyword-only detail flag and deterministic output.

## Prerequisites
Functions, keyword arguments, strings, conditionals, and validation.

## Scenario Introduction
A simulated diagnostic report needs compact or detailed messages for an operator.

## Problem Statement
**Goal:** Define a formatting function with a keyword-only detail flag and deterministic output.

**Specifically:** Format a normalized diagnostic message with optional measured value and units.

## Task to Implement
Implement `format_diagnostic(code: str, severity: str, message: str, *, value: float | None = None, units: str = "", detailed: bool = False) -> str`.

## Input Specification
Code is 2 to 12 alphanumeric or hyphen characters, severity is `INFO`, `WARNING`, or `CRITICAL`, and message is non-empty. If value is provided it is finite; units must be non-empty when value is provided. Detailed is boolean.

## Output Specification
Compact output is `[SEVERITY] CODE: MESSAGE`. Detailed output appends ` | value=VALUE UNITS` when value exists, with value rounded to two decimals and no trailing unit space.

## Rules and Constraints
- Normalize code and severity to uppercase and trim message.
- `value`, `units`, and `detailed` are keyword-only.
- Raise `ValueError` for invalid input; do not use external systems.

## Hints
1. Normalize fields before assembling the string.
2. Check the value and units relationship together.
3. Use a conditional suffix for detailed measured data.

## Common Mistakes
- Allowing positional arguments after `*`.
- Adding a trailing space when units are absent.
- Rounding the message's source value in place.

## Extension Challenge
Add a keyword-only timestamp in integer milliseconds while preserving compact output.
