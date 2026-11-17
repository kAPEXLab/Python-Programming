# 04_Strings_VINDisplay

**Difficulty:** Easy  
**Primary Python Concept:** Strings  
**Supporting Concepts:** String methods, validation, formatting  
**Automotive Domain:** Vehicle identification number (VIN) display  
**Estimated Completion Time:** 20 minutes

## Learning Objective
Normalize and validate a vehicle identifier using basic string operations.

## Prerequisites
Strings, methods, conditionals, functions, and formatted output.

## Scenario Introduction
A VIN is a 17-character identifier for a vehicle. This exercise uses a simplified rule: the VIN may contain uppercase letters and digits, but not spaces or punctuation.

## Problem Statement
**Goal:** Normalize and validate a vehicle identifier using basic string operations.

**Specifically:** Normalize a VIN and display it in grouped blocks for a workshop screen.

## Task to Implement
Implement `format_vin(vin: str) -> str`. Strip surrounding whitespace, convert letters to uppercase, validate the normalized VIN, and return groups of 4, 4, 4, and 5 characters separated by hyphens.

## Input Specification
`vin` must normalize to exactly 17 uppercase letters or digits. Reject invalid input with `ValueError`.

## Output Specification
Return a string such as `WVWZ-ZZ1J-ZXW0-00001`.

## Rules and Constraints
- Use string methods and a clear function.
- Do not silently remove internal spaces or punctuation.
- Preserve digits.

## Hints
1. Normalize only outer whitespace and case.
2. Validate length and allowed characters.
3. Use slices to create four groups.

## Common Mistakes
- Removing internal spaces.
- Producing groups of equal length.
- Forgetting lowercase input.

## Extension Challenge
Mask characters 9 through 12 with `*` for a privacy-safe display.
