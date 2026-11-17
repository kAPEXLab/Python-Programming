# 38_RaisingAndCustomExceptions_InvalidDTC

**Difficulty:** Medium
**Primary Python Concept:** Raising and defining custom exceptions  
**Supporting Concepts:** Regular expressions, exception payloads, parsing, validation  
**Automotive Domain:** Offline diagnostic trouble code validation  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Create a custom validation exception and use it to protect a diagnostic-code parser.

## Prerequisites
Exceptions, classes, strings, regular expressions, and functions.

## Scenario Introduction
A diagnostic report accepts standardized DTC-like codes but must identify malformed entries clearly.

## Problem Statement
**Goal:** Create a custom validation exception and use it to protect a diagnostic-code parser.

**Specifically:** Define `InvalidDTC(Exception)` and implement `normalize_dtc(raw: str) -> str`.

## Task to Implement
Strip surrounding whitespace, uppercase the code, and accept exactly one letter from `P`, `B`, `C`, or `U` followed by four hexadecimal characters. Raise `InvalidDTC` with the original input for any failure.

## Input Specification
Input must be a string. Valid examples include `p0420` and `U0100`.

## Output Specification
Return the normalized uppercase code.

## Rules and Constraints
- Preserve the original invalid value in the exception.
- Do not accept internal whitespace or six-character codes.
- Do not query a real diagnostic interface.

## Hints
Compile one anchored regular expression and match the normalized value.

## Common Mistakes
- Accepting arbitrary letters.
- Removing internal spaces.
- Losing the original input in the exception.

## Extension Challenge
Add a parsed `system` property to the exception.
