# 07_MatchCase_DiagnosticStatus

**Difficulty:** Easy  
**Primary Python Concept:** `match-case` statements  
**Supporting Concepts:** Strings, validation, return values  
**Automotive Domain:** Vehicle diagnostics  
**Estimated Completion Time:** 25 minutes

## Learning Objective
Use structural pattern matching to map discrete diagnostic codes to status labels.

## Prerequisites
Functions, strings, conditionals, and basic validation.

## Scenario Introduction
A diagnostic trouble code (DTC) is a short code representing a detected issue. This offline exercise uses four simulated codes.

## Problem Statement
**Goal:** Use structural pattern matching to map discrete diagnostic codes to status labels.

**Specifically:** Translate a DTC into a dashboard status.

## Task to Implement
Implement `diagnostic_status(code: str) -> str` using `match-case`. Accepted codes are `P0000`, `P0300`, `B0001`, and `U0100`.

## Input Specification
`code` must be a non-empty string. Matching is case-insensitive after trimming whitespace. Unknown codes are valid inputs.

## Output Specification
Return `CLEAR`, `ENGINE_MISFIRE`, `BODY_SENSOR_FAULT`, `COMMUNICATION_FAULT`, or `UNKNOWN_CODE`.

## Rules and Constraints
- Use `match-case`, not a long `if-elif` chain.
- Normalize whitespace and case once.
- Raise `ValueError` for a blank code.

## Hints
1. Normalize the code before matching.
2. Add one case for each known code.
3. Use `_` for unknown values.

## Common Mistakes
- Forgetting case normalization.
- Treating unknown codes as errors.
- Using pattern matching syntax incorrectly.

## Extension Challenge
Return a tuple containing the status and a severity label.
