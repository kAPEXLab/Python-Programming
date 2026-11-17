---
layout: default
---

# 48_DecoratorsAndClosures_AccessAudit

**Difficulty:** Difficult  
**Primary Python Concept:** Stateful decorators and closures  
**Supporting Concepts:** Nonlocal state, authorization, metadata  
**Automotive Domain:** Offline diagnostic access audit  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Track permitted and denied calls through a closure without global mutable state.

## Prerequisites
Decorators, closures, `nonlocal`, functions, and exceptions.

## Scenario Introduction
A simulated workshop API records how many diagnostic calls each decorated function receives.

## Problem Statement
**Goal:** Track permitted and denied calls through a closure without global mutable state.

**Specifically:** Implement `audit_access(role: str) -> Callable` and decorate functions accepting `user: str`.

## Task to Implement
Allow roles `technician` and `engineer`; reject `guest` and any other unknown non-empty role with `PermissionError`. The decorator exposes `calls() -> int`, counting only permitted calls.

## Input Specification
Role and user are non-empty strings; calls use keyword or positional user values.

## Output Specification
Return the wrapped result for permitted calls and maintain an isolated count per decorated function.

## Rules and Constraints
- Store the counter in a closure using `nonlocal`.
- Do not use a module-level counter.
- Access is simulated and cannot control a vehicle.

## Hints
Validate role when creating the decorator and increment only inside the authorized path.

## Common Mistakes
- Sharing state across decorated functions.
- Incrementing before authorization.
- Returning a mutable global counter.

## Extension Challenge
Expose separate permitted and denied counters.
