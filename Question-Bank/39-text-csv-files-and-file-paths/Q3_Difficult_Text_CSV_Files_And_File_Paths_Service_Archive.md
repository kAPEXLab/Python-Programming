---
layout: default
---

# 39_TextCSVFilesAndFilePaths_ServiceArchive

**Difficulty:** Difficult
**Primary Python Concept:** Text CSV files and file paths  
**Supporting Concepts:** CSV schema validation, `pathlib`, filtering, file errors  
**Automotive Domain:** Offline service history archive  
**Estimated Completion Time:** 65 minutes

## Learning Objective
Build a validated CSV service archive with selective record loading.

## Prerequisites
CSV readers and writers, paths, dictionaries, filtering, and exceptions.

## Scenario Introduction
A local archive stores service visits that can be queried by vehicle ID.

## Problem Statement
**Goal:** Build a validated CSV service archive with selective record loading.

**Specifically:** Implement `save_services(path: Path, records: list[dict[str, object]]) -> None` and `load_vehicle_services(path: Path, vehicle_id: str) -> list[dict[str, str]]`.

## Task to Implement
Use columns `vehicle_id,date,odometer_km,operation`. Validate ISO dates, non-negative integer odometers, and non-empty text. Return matching rows in file order.

## Input Specification
Vehicle ID and operation are non-empty. Dates use `YYYY-MM-DD`; odometer is an integer from 0 upward.

## Output Specification
Save returns `None`; load returns matching string-valued rows.

## Rules and Constraints
- Validate all records before writing.
- Use only local paths and UTF-8 CSV.
- Raise `ValueError` for malformed records and `FileNotFoundError` for absent archives.

## Hints
Use `date.fromisoformat` to validate dates, then write original ISO text.

## Common Mistakes
- Returning rows for every vehicle.
- Validating only the first record.
- Treating file paths as raw string concatenation.

## Extension Challenge
Add a date-range query using inclusive endpoints.
