# 43_ModulesAndPackages_DiagnosticToolkit

**Difficulty:** Medium  
**Primary Python Concept:** Package structure and re-exports  
**Supporting Concepts:** `__init__.py`, submodules, public API design  
**Automotive Domain:** Offline diagnostic toolkit  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Design a small package that exposes a clean diagnostic API over specialized submodules.

## Prerequisites
Modules, imports, dictionaries, functions, and exceptions.

## Scenario Introduction
A diagnostic toolkit package separates code lookup from severity classification.

## Problem Statement
**Goal:** Design a small package that exposes a clean diagnostic API over specialized submodules.

**Specifically:** Create package modules `codes.py` and `severity.py`, then expose `describe_code(code: str) -> str` from the package.

## Task to Implement
Map `P0420` to `CATALYST_EFFICIENCY`, `P0301` to `CYLINDER_1_MISFIRE`, and unknown codes to `UNKNOWN_CODE`. Normalize case and whitespace.

## Input Specification
`code` must be a non-empty string containing a diagnostic code.

## Output Specification
Return the exact symbolic description as a string.

## Rules and Constraints
- The package root must re-export the public function.
- Keep code data in its own submodule.
- No live diagnostic interface is permitted.

## Hints
Normalize once at the package boundary and use a dictionary lookup.

## Common Mistakes
- Importing from a file path instead of the package API.
- Mutating the code catalog during lookup.
- Raising for every unknown code.

## Extension Challenge
Expose `severity_for(code: str) -> str` from a second package submodule.
