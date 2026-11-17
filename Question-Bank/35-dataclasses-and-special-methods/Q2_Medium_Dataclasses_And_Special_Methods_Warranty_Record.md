# 35_DataclassesAndSpecialMethods_WarrantyRecord

**Difficulty:** Medium
**Primary Python Concept:** Dataclasses and special methods  
**Supporting Concepts:** Default fields, date arithmetic, validation, formatting  
**Automotive Domain:** Offline warranty records  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Model warranty data with dataclass defaults and a domain-specific special method.

## Prerequisites
Dataclasses, `datetime.date`, methods, and comparisons.

## Scenario Introduction
A service archive needs deterministic warranty records that can report whether coverage applies on a date.

## Problem Statement
**Goal:** Model warranty data with dataclass defaults and a domain-specific special method.

**Specifically:** Define dataclass `WarrantyRecord` with `vehicle_id: str`, `start: date`, `months: int`, and `mileage_limit_km: int`. Implement `is_active(on_date: date, mileage_km: int) -> bool` and `label() -> str`.

## Task to Implement
Coverage includes the start date and ends on the last day before the month anniversary. Mileage is covered through the inclusive limit. Label format is `ID: YYYY-MM-DD for N months / M km`.

## Input Specification
IDs are non-empty. Months are 1 through 120; mileage limit is non-negative; mileage is non-negative.

## Output Specification
Return a boolean from `is_active` and the exact label format from `label`.

## Rules and Constraints
- Store dates as `datetime.date`, not strings.
- Raise `ValueError` for invalid months or mileage.
- No current-date lookup; every date is supplied.

## Hints
Use calendar month arithmetic rather than approximating a month as 30 days.

## Common Mistakes
- Using today's date implicitly.
- Excluding the start date.
- Treating mileage limit as exclusive.

## Extension Challenge
Add a method that returns remaining months and kilometers.
