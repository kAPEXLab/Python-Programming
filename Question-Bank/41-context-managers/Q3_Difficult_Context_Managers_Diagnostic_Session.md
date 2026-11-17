---
layout: default
---

# 41_ContextManagers_DiagnosticSession

**Difficulty:** Difficult
**Primary Python Concept:** Context managers  
**Supporting Concepts:** Nested resources, transaction-like cleanup, validation, exception propagation  
**Automotive Domain:** Offline diagnostic session lifecycle  
**Estimated Completion Time:** 65 minutes

## Learning Objective
Coordinate session start and end states reliably with a context manager.

## Prerequisites
Context-manager protocol, classes, lists, exceptions, and state machines.

## Scenario Introduction
A simulated diagnostic session records commands only while the session is active.

## Problem Statement
**Goal:** Coordinate session start and end states reliably with a context manager.

**Specifically:** Implement `DiagnosticSession(vehicle_id: str)` with `__enter__`, `__exit__`, `send(command: str) -> str`, and `commands() -> tuple[str, ...]`.

## Task to Implement
Entering starts the session. `send` accepts non-empty uppercase commands and returns `ACK:<command>`. Exiting ends the session and freezes the command history. Body exceptions must propagate.

## Input Specification
Vehicle ID and commands are non-empty strings. Commands must match uppercase letters, digits, and underscores only.

## Output Specification
Return acknowledgements from `send`; after exit, `commands()` returns an immutable tuple in order.

## Rules and Constraints
- Sending before entry or after exit raises `RuntimeError`.
- Invalid commands raise `ValueError` without being recorded.
- This is an offline simulation and must not open a vehicle connection.

## Hints
Use a private mutable list during the session and expose a tuple afterward.

## Common Mistakes
- Recording invalid commands.
- Allowing commands after exit.
- Suppressing exceptions in `__exit__`.

## Extension Challenge
Add a maximum session duration supplied as a deterministic integer limit.
