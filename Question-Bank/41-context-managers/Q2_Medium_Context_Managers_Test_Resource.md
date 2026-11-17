---
layout: default
---

# 41_ContextManagers_TestResource

**Difficulty:** Medium
**Primary Python Concept:** Context managers  
**Supporting Concepts:** Resource lifecycle, state flags, exception propagation, testing  
**Automotive Domain:** Offline test-resource reservation  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Guarantee acquisition and release of a simulated test resource through a context manager.

## Prerequisites
Classes, `with`, methods, state validation, and exceptions.

## Scenario Introduction
A test harness reserves a named resource for one simulated test at a time.

## Problem Statement
**Goal:** Guarantee acquisition and release of a simulated test resource through a context manager.

**Specifically:** Implement `TestResource(name: str)` with `__enter__`, `__exit__`, `use(label: str) -> str`, and `released: bool`.

## Task to Implement
Entering marks the resource active; `use` returns `name:label`; exiting marks it released. Use outside the context raises `RuntimeError`. Do not suppress body exceptions.

## Input Specification
Name and label are non-empty strings. A resource starts unreleased and inactive.

## Output Specification
Return the exact `name:label` string from valid use.

## Rules and Constraints
- Release must happen even when the body raises.
- A resource cannot be entered twice without a matching exit.
- This resource is entirely simulated.

## Hints
Track active and released state separately; cleanup belongs in `__exit__`.

## Common Mistakes
- Releasing only on successful exit.
- Returning `True` from `__exit__`.
- Allowing use before acquisition.

## Extension Challenge
Add an acquisition counter for repeated sequential uses.
