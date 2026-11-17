---
layout: default
---

# 39_TextCSVFilesAndFilePaths_InspectionReport

**Difficulty:** Medium
**Primary Python Concept:** Text CSV files and file paths  
**Supporting Concepts:** `pathlib`, CSV dictionaries, deterministic aggregation, validation  
**Automotive Domain:** Offline inspection report export  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Create a CSV inspection report and calculate a pass count from its records.

## Prerequisites
CSV, file paths, dictionaries, loops, and numeric conversion.

## Scenario Introduction
A workshop simulator records inspection checks in a local report file.

## Problem Statement
**Goal:** Create a CSV inspection report and calculate a pass count from its records.

**Specifically:** Implement `export_inspections(path: Path, rows: list[dict[str, object]]) -> None` and `count_passes(path: Path) -> int`.

## Task to Implement
Use columns `vehicle_id,check,status`. Status must be `PASS` or `FAIL`. Count exact `PASS` rows without changing their order or text.

## Input Specification
IDs and checks are non-empty strings. Rows must have all three columns.

## Output Specification
Export returns `None`; count returns an integer.

## Rules and Constraints
- Use UTF-8 and `csv.DictWriter`/`DictReader`.
- Paths must be handled with `pathlib.Path`.
- Raise `ValueError` for missing fields or unknown status.

## Hints
Validate rows before opening the output file so failed input cannot create a partial report.

## Common Mistakes
- Counting case-insensitive statuses.
- Writing a partial file before validation.
- Using string concatenation for CSV.

## Extension Challenge
Add a function that returns failed check names by vehicle.
