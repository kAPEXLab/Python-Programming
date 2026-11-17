---
layout: default
---

# 44_MainGuardAndStandardLibrary_TestRunner

**Difficulty:** Difficult  
**Primary Python Concept:** `unittest` and executable module guards  
**Supporting Concepts:** Test discovery, `unittest.mock`, exit status  
**Automotive Domain:** Offline diagnostic test runner  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Create a small standard-library test runner that can be imported without starting tests.

## Prerequisites
Classes, functions, `unittest`, mocks, and the main guard.

## Scenario Introduction
A diagnostic team needs a deterministic runner for a local suite of simulated checks.

## Problem Statement
**Goal:** Create a small standard-library test runner that can be imported without starting tests.

**Specifically:** Implement `run_checks(loader: unittest.TestLoader, runner: unittest.TestRunner, suite: unittest.TestSuite) -> bool`.

## Task to Implement
Run the supplied suite and return `True` only when the result is successful. Do not call discovery or execute tests at import time.

## Input Specification
The loader, runner, and suite are standard `unittest` objects or compatible test doubles.

## Output Specification
Return a boolean success value and leave test output to the supplied runner.

## Rules and Constraints
- Use `unittest` from the standard library.
- Keep the entry point under `if __name__ == "__main__"`.
- Tests are local simulations only.

## Hints
Call `runner.run(suite)` once and inspect only `wasSuccessful()`.

## Common Mistakes
- Returning the result object instead of a boolean.
- Running tests while importing the module.
- Rebuilding a caller-supplied suite.

## Extension Challenge
Add a command-line switch that selects one named test suite.
