---
layout: default
---

# 41_ContextManagers_LogCapture

**Difficulty:** Easy
**Primary Python Concept:** Context managers  
**Supporting Concepts:** `__enter__`, `__exit__`, `io.StringIO`, exception propagation  
**Automotive Domain:** Offline diagnostic log capture  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Implement a context manager that captures simulated diagnostic messages and closes its resource correctly.

## Prerequisites
Classes, context managers, strings, and exceptions.

## Scenario Introduction
A test harness captures diagnostic text during a simulated scan without writing to a real vehicle interface.

## Problem Statement
**Goal:** Implement a context manager that captures simulated diagnostic messages and closes its resource correctly.

**Specifically:** Implement `LogCapture` with `__enter__`, `__exit__`, `write(message: str) -> None`, and `text() -> str`.

## Task to Implement
Capture messages separated by newlines. `text()` returns the captured text. The context manager must close its internal stream on exit and must not suppress exceptions.

## Input Specification
Messages must be strings. Empty messages are allowed and still produce a line.

## Output Specification
Return exact captured text with one newline per write.

## Rules and Constraints
- Use `io.StringIO` internally.
- Writes after exit must raise `ValueError`.
- Do not connect to hardware or suppress exceptions.

## Hints
Return `self` from `__enter__` and close in `__exit__`.

## Common Mistakes
- Suppressing exceptions by returning `True`.
- Forgetting to close the stream.
- Joining messages without a trailing newline.

## Extension Challenge
Add a maximum message count and raise `OverflowError` beyond it.
