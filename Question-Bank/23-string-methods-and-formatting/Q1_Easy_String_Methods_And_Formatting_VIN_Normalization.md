# 23_StringMethodsAndFormatting_VINNormalization

**Difficulty:** Easy
**Primary Python Concept:** String methods and formatting  
**Supporting Concepts:** Validation, slicing, case conversion  
**Automotive Domain:** Offline vehicle identification display  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Normalize a vehicle identification string while applying strict character and length rules.

## Prerequisites
Strings, slicing, methods, conditionals, and exceptions.

## Scenario Introduction
A simulated inventory screen receives VIN text from multiple operators with inconsistent spacing and case.

## Problem Statement
**Goal:** Normalize a vehicle identification string while applying strict character and length rules.

**Specifically:** Return a display-ready VIN after trimming separators and uppercasing letters.

## Task to Implement
Implement `normalize_vin(raw_vin: str) -> str`.

## Input Specification
The input may contain surrounding whitespace and internal hyphens or spaces. After removing spaces and hyphens, it must contain exactly 17 uppercase letters or digits, excluding `I`, `O`, and `Q`.

## Output Specification
Return the 17-character uppercase VIN with separators removed.

## Rules and Constraints
- Accept only a string.
- Do not use external VIN services.
- Raise `ValueError` for invalid length or characters.

## Hints
1. Remove spaces and hyphens before checking length.
2. Convert to uppercase once.
3. Validate against the permitted character set.

## Common Mistakes
- Counting separators toward the length.
- Allowing `I`, `O`, or `Q`.
- Returning the original casing.

## Extension Challenge
Format a normalized VIN as groups of 3, 6, and 8 characters for a printed label.
