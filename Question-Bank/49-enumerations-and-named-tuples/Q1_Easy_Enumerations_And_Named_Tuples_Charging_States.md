# 49_EnumerationsAndNamedTuples_ChargingStates

**Difficulty:** Easy  
**Primary Python Concept:** `Enum`  
**Supporting Concepts:** Members, comparisons, serialization  
**Automotive Domain:** Offline charging states  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Represent charging modes with a type-safe enumeration.

## Prerequisites
Classes, strings, functions, and comparisons.

## Scenario Introduction
A prerecorded charging session reports one of a fixed set of states.

## Problem Statement
**Goal:** Represent charging modes with a type-safe enumeration.

**Specifically:** Define `ChargingState(Enum)` with `IDLE`, `PLUGGED`, `CHARGING`, and `COMPLETE`, each using its lowercase name as value, plus `parse_state(text: str) -> ChargingState`.

## Task to Implement
Normalize text and return the matching enum member; raise `ValueError` for unknown text.

## Input Specification
Text is a non-empty state name, case-insensitive after stripping.

## Output Specification
Return a `ChargingState` member.

## Rules and Constraints
- Compare enum members, not ad hoc strings, after parsing.
- Keep states finite and deterministic.
- No charger connection is required.

## Hints
Use enum values as the normalized lookup keys.

## Common Mistakes
- Returning the input string.
- Adding a catch-all enum member.
- Forgetting whitespace normalization.

## Extension Challenge
Add a `terminal` property for `IDLE` and `COMPLETE`.
