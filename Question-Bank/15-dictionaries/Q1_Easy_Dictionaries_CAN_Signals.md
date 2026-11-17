# 15_Dictionaries_CANSignals

**Difficulty:** Easy  
**Primary Python Concept:** Dictionary keys and values  
**Supporting Concepts:** Lookup, validation, strings, functions  
**Automotive Domain:** Simulated CAN signal registry  
**Estimated Completion Time:** 25 minutes

## Learning Objective
Use dictionary lookups to retrieve named signal values safely.

## Prerequisites
Dictionaries, strings, numbers, functions, and conditionals.

## Scenario Introduction
An offline data fixture maps signal names to their current numeric readings.

## Problem Statement
**Goal:** Use dictionary lookups to retrieve named signal values safely.

**Specifically:** Return the requested signal value and a clear missing-signal result.

## Task to Implement
Implement `read_can_signal(signals: dict[str, float], name: str) -> float | None`.

## Input Specification
Signal names are non-empty strings. Values are finite numbers from -1000.0 through 1000.0. The requested name may include surrounding whitespace and is case-insensitive.

## Output Specification
Return the matching numeric value or `None` when no normalized key exists.

## Rules and Constraints
- Normalize only the requested name and compare signal names case-insensitively.
- Reject malformed dictionaries or names with `ValueError`.
- Do not mutate input.

## Hints
1. Validate all dictionary entries first.
2. Strip and uppercase the requested name.
3. Search normalized keys without changing the source dictionary.

## Common Mistakes
- Raising `KeyError` for a missing signal.
- Mutating keys during normalization.
- Treating zero as missing.

## Extension Challenge
Return both the value and the normalized key as a tuple.
