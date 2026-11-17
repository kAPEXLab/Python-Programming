---
layout: default
---

# 22_TypeHintsDocstringsAndPureFunctions_DiagnosticLibrary

**Difficulty:** Difficult
**Primary Python Concept:** Type hints, docstrings, and pure functions  
**Supporting Concepts:** Dictionaries, optional values, lookup rules  
**Automotive Domain:** Offline diagnostic-code descriptions  
**Estimated Completion Time:** 40 minutes

## Learning Objective
Use typed inputs and outputs to create a predictable diagnostic lookup function.

## Prerequisites
Functions, dictionaries, strings, `None`, and validation.

## Scenario Introduction
A workshop simulator stores a small library of fault codes and descriptions. A lookup must not access a real diagnostic network.

## Problem Statement
**Goal:** Use typed inputs and outputs to create a predictable diagnostic lookup function.

**Specifically:** Look up a normalized code and produce a fallback message for an unknown but well-formed code.

## Task to Implement
Implement `describe_code(code: str, library: dict[str, str]) -> str` with a docstring.

## Input Specification
Code must be a non-empty string of 2 to 8 letters, digits, or hyphens. Normalize it by trimming and uppercasing. Library keys are expected to be uppercase.

## Output Specification
Return the matching description, or `Unknown diagnostic code: CODE` when the code is absent.

## Rules and Constraints
- Do not mutate the library.
- Reject non-string codes, malformed codes, or non-string library keys and values with `ValueError`.
- The function must be deterministic and side-effect free.

## Hints
1. Validate the code before normalizing it.
2. Use `dict.get` or membership testing for the fallback.
3. Preserve the caller's dictionary.

## Common Mistakes
- Looking up the unnormalized code.
- Returning `None` for an unknown code.
- Silently accepting invalid library entries.

## Extension Challenge
Add a pure function that returns all library codes sorted alphabetically.
