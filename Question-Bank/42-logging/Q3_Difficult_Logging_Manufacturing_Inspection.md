---
layout: default
---

# 42_Logging_ManufacturingInspection

**Difficulty:** Difficult  
**Primary Python Concept:** Structured logging with contextual fields  
**Supporting Concepts:** `LoggerAdapter`, exception logging, deterministic records  
**Automotive Domain:** Offline manufacturing inspection  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Use contextual logging to make inspection outcomes traceable without exposing proprietary information.

## Prerequisites
Logging, classes, dictionaries, validation, and exception handling.

## Scenario Introduction
A simulated manufacturing station inspects a component and needs the station and part number in every log record.

## Problem Statement
**Goal:** Use contextual logging to make inspection outcomes traceable without exposing proprietary information.

**Specifically:** Implement `ManufacturingInspection(logger: logging.Logger, station: str)` with `inspect(part_number: str, measured_mm: float) -> str`.

## Task to Implement
Accept measurements from 9.95 through 10.05 mm inclusive, log `INFO`, and return `PASS:<part_number>`. Otherwise log `WARNING` and return `REJECT:<part_number>`. Malformed input raises `ValueError` and logs `ERROR`.

## Input Specification
`station` and `part_number` are non-empty strings. `measured_mm` is finite and numeric.

## Output Specification
Return the exact pass or reject result. Every record must carry `station` and `part_number` context.

## Rules and Constraints
- Use a logger adapter or an equivalent structured `extra` mapping.
- Do not log secrets or real manufacturing data.
- Boundary comparisons are inclusive.

## Hints
Build context once, validate types before comparisons, and keep severity tied to the outcome.

## Common Mistakes
- Comparing numeric strings silently.
- Omitting context from error records.
- Treating tolerance endpoints as rejected.

## Extension Challenge
Add a `reason` field to every rejected inspection record.
