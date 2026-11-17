# 23_StringMethodsAndFormatting_FaultMessages

**Difficulty:** Difficult
**Primary Python Concept:** String methods and formatting  
**Supporting Concepts:** Replacement, capitalization, templates  
**Automotive Domain:** Offline dashboard fault messages  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Compose concise fault messages from normalized text fields.

## Prerequisites
String methods, f-strings, dictionaries, and validation.

## Scenario Introduction
A dashboard prototype converts a fault code, severity, and component into one consistent operator message.

## Problem Statement
**Goal:** Compose concise fault messages from normalized text fields.

**Specifically:** Normalize the fields and render a fixed message template.

## Task to Implement
Implement `build_fault_message(code: str, severity: str, component: str) -> str`.

## Input Specification
Code is 2 to 8 alphanumeric or hyphen characters. Severity is `info`, `warning`, or `critical`, case-insensitive. Component is non-empty text.

## Output Specification
Return `SEVERITY: CODE - Component requires attention`, where severity and code are uppercase and component uses trimmed title case.

## Rules and Constraints
- Collapse repeated whitespace in the component.
- Reject unsupported severity, malformed code, or empty component with `ValueError`.
- Do not print or connect to a dashboard.

## Hints
1. Normalize code and severity independently.
2. Use `split` and `join` before title-casing the component.
3. Validate severity using a set of allowed values.

## Common Mistakes
- Title-casing the fault code.
- Accepting arbitrary severity text.
- Treating whitespace as a component name.

## Extension Challenge
Allow an optional measured value and unit while keeping the original output unchanged when omitted.
