# 39_TextCSVFilesAndFilePaths_FleetTrips

**Difficulty:** Easy
**Primary Python Concept:** Text CSV files and file paths  
**Supporting Concepts:** `pathlib`, `csv`, validation, context managers  
**Automotive Domain:** Offline fleet trip archive  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Read and write deterministic CSV trip records using safe local paths.

## Prerequisites
Functions, lists, dictionaries, `pathlib`, and CSV basics.

## Scenario Introduction
A simulator exports fleet trips for later analysis without contacting a vehicle or service.

## Problem Statement
**Goal:** Read and write deterministic CSV trip records using safe local paths.

**Specifically:** Implement `write_trips(path: Path, trips: list[dict[str, object]]) -> None` and `read_trips(path: Path) -> list[dict[str, str]]`.

## Task to Implement
Write header `vehicle_id,distance_km,energy_kwh` and rows in input order. Read the same header and return string-valued dictionaries.

## Input Specification
IDs are non-empty; distances and energy are non-negative finite numbers. Paths are local filesystem paths.

## Output Specification
Writing returns `None`; reading returns rows in file order.

## Rules and Constraints
- Use `pathlib.Path` and `csv`, not manual comma joins.
- Use UTF-8 text and newline handling suitable for CSV.
- Raise `ValueError` for invalid trip records and `FileNotFoundError` for absent files.

## Hints
Let `csv.DictWriter` and `csv.DictReader` manage quoting and headers.

## Common Mistakes
- Splitting lines on commas manually.
- Omitting the header.
- Converting values during a function specified to return strings.

## Extension Challenge
Add a `started_at` ISO date column.
