---
layout: default
---

# 38_RaisingAndCustomExceptions_ChargingConflict

**Difficulty:** Difficult
**Primary Python Concept:** Raising and defining custom exceptions  
**Supporting Concepts:** Exception chaining, state validation, domain rules, type hints  
**Automotive Domain:** Offline charging-state conflict detection  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Raise a meaningful custom exception when mutually exclusive charging states are requested.

## Prerequisites
Custom exceptions, dictionaries, boolean logic, and exception chaining.

## Scenario Introduction
A simulator receives charging commands from two independent scheduling sources.

## Problem Statement
**Goal:** Raise a meaningful custom exception when mutually exclusive charging states are requested.

**Specifically:** Define `ChargingConflict(Exception)` and implement `resolve_charging_request(request: dict[str, object]) -> str`.

## Task to Implement
The request must contain `mode` (`AC`, `DC`, or `OFF`) and `scheduled` (`bool`). `DC` with `scheduled=True` raises `ChargingConflict`; `OFF` returns `DISABLED`; all other valid states return `READY`.

## Input Specification
Mode must be an exact uppercase string and scheduled must be boolean. Missing fields should be reported as `KeyError`.

## Output Specification
Return `READY` or `DISABLED` exactly, or raise the specified exception.

## Rules and Constraints
- Include both conflicting fields in the custom exception message.
- Preserve `KeyError` for missing required fields.
- Keep all behavior offline.

## Hints
Extract required fields before applying the domain conflict rule.

## Common Mistakes
- Treating `1` as boolean `True`.
- Returning a normal status for a conflict.
- Hiding missing keys behind defaults.

## Extension Challenge
Chain a lower-level parsing error into `ChargingConflict`.
