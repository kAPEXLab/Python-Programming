# 49_EnumerationsAndNamedTuples_DiagnosticSeverity

**Difficulty:** Difficult  
**Primary Python Concept:** Enums combined with named tuples  
**Supporting Concepts:** Ordered severity, immutable records, parsing  
**Automotive Domain:** Offline diagnostic severity  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Represent diagnostic events as immutable records with a controlled severity enum.

## Prerequisites
Enums, named tuples, validation, and ordering.

## Scenario Introduction
A report ranks synthetic diagnostic events without relying on arbitrary severity strings.

## Problem Statement
**Goal:** Represent diagnostic events as immutable records with a controlled severity enum.

**Specifically:** Define `Severity(IntEnum)` with `INFO=1`, `WARNING=2`, `CRITICAL=3`, and `DiagnosticEvent(NamedTuple)` with `code: str`, `severity: Severity`.

## Task to Implement
Implement `parse_event(code: str, severity: str) -> DiagnosticEvent`, normalizing severity and rejecting blank codes or unknown levels.

## Input Specification
Codes are non-empty strings; severity is `info`, `warning`, or `critical`, case-insensitive.

## Output Specification
Return a `DiagnosticEvent` with the matching enum member.

## Rules and Constraints
- Use `IntEnum` for meaningful comparisons.
- Keep records immutable.
- Events are synthetic and offline.

## Hints
Use a normalized value-to-member mapping and validate the code separately.

## Common Mistakes
- Comparing unrelated strings for ranking.
- Mutating event fields.
- Treating `fatal` as an implicit alias.

## Extension Challenge
Add a function that returns the most severe event from an iterable.
