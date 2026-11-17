# 44_MainGuardAndStandardLibrary_ReportGenerator

**Difficulty:** Easy  
**Primary Python Concept:** `if __name__ == "__main__"`  
**Supporting Concepts:** `pathlib`, `statistics`, import-safe scripts  
**Automotive Domain:** Offline report generation  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Build a script that is reusable when imported and executable when run directly.

## Prerequisites
Functions, imports, lists, `pathlib`, and basic module execution.

## Scenario Introduction
A report generator summarizes a fixed set of fleet distances without running work during import.

## Problem Statement
**Goal:** Build a script that is reusable when imported and executable when run directly.

**Specifically:** Implement `build_report(distances_km: list[float]) -> str` and a guarded `main() -> None`.

## Task to Implement
Return `COUNT=<n>;AVERAGE_KM=<average:.1f>` using `statistics.fmean`. Reject an empty list and negative values.

## Input Specification
Distances are finite, non-negative floats in kilometers.

## Output Specification
Return one deterministic summary string; `main` prints it only when the file is run as a script.

## Rules and Constraints
- Keep execution behind the main guard.
- Use the standard library only.
- No file or vehicle connection is needed.

## Hints
Put only the call to `main()` under the guard; imports must remain safe.

## Common Mistakes
- Calling `main()` at import time.
- Using a hand-written average with an empty list.
- Formatting the count as a decimal.

## Extension Challenge
Add a report path using `pathlib.Path` without writing during import.
