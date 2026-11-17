---
layout: default
---

# 07_MatchCase_ChargingMode

**Difficulty:** Medium  
**Primary Python Concept:** `match-case` with guarded patterns  
**Supporting Concepts:** Dictionaries, validation, numeric comparisons  
**Automotive Domain:** Electric-vehicle charging  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Use pattern matching and guards to classify a charging request.

## Prerequisites
`match-case`, functions, dictionaries, comparisons, and exceptions.

## Scenario Introduction
A charging station receives a simulated request containing connector type and requested current. AC charging supports up to 32 A; DC fast charging supports up to 200 A.

## Problem Statement
**Goal:** Use pattern matching and guards to classify a charging request.

**Specifically:** Return the charging mode and whether the request is accepted.

## Task to Implement
Implement `evaluate_charging_request(request: dict[str, object]) -> str`. Required fields are `connector` (`AC` or `DC`) and `current_a`.

## Input Specification
Current must be 0 through 200 A. AC current must be at most 32 A. DC current may be 0 through 200 A. A non-empty connector other than `AC` or `DC` returns `UNKNOWN_CONNECTOR`; missing, blank, non-string, or otherwise malformed required fields raise `ValueError`.

## Output Specification
Return `AC_ACCEPTED`, `DC_ACCEPTED`, `AC_CURRENT_TOO_HIGH`, `DC_CURRENT_TOO_HIGH`, or `UNKNOWN_CONNECTOR`.

## Rules and Constraints
- Use `match-case` on the connector.
- Treat connector matching as case-insensitive.
- Unknown non-empty connector values are not malformed and return `UNKNOWN_CONNECTOR`.
- Current exactly at the limit is accepted.

## Hints
1. Validate the dictionary shape before matching.
2. Normalize the connector value.
3. Use a guard to compare current against 32 A.

## Common Mistakes
- Applying the AC limit to DC.
- Accepting missing fields as zero.
- Making the limit exclusive.

## Extension Challenge
Support a `THREE_PHASE_AC` connector with a 63 A limit.
