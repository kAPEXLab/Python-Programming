---
layout: default
---

# 10_LoopControl_FaultScanning

**Difficulty:** Easy  
**Primary Python Concept:** `break`  
**Supporting Concepts:** Lists, strings, validation, searching  
**Automotive Domain:** Diagnostic fault scanning  
**Estimated Completion Time:** 20 minutes

## Learning Objective
Use `break` to stop a scan at the first critical simulated fault.

## Prerequisites
Lists, loops, conditionals, strings, and functions.

## Scenario Introduction
A diagnostic scan checks DTC labels in order. `CRITICAL` means the scan should stop immediately; other labels are noncritical.

## Problem Statement
**Goal:** Use `break` to stop a scan at the first critical simulated fault.

**Specifically:** Return the index of the first critical fault, or `None` when none exists.

## Task to Implement
Implement `find_first_critical(fault_levels: list[str]) -> int | None`.

## Input Specification
List length is 0 through 10,000. Each label is `INFO`, `WARNING`, or `CRITICAL`, case-insensitive. Reject invalid values with `ValueError`.

## Output Specification
Return the zero-based index of the first `CRITICAL`, or `None`.

## Rules and Constraints
- Use `break` to stop after the first critical entry.
- Preserve input order.
- Do not use `list.index()` as a shortcut.

## Hints
1. Track the index with `enumerate()`.
2. Break when the normalized label is critical.
3. Keep a result variable initialized to `None`.

## Common Mistakes
- Returning the last critical index.
- Continuing after the first critical fault.
- Forgetting empty input.

## Extension Challenge
Return the number of records inspected as well as the index.
