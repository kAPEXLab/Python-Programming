---
layout: default
---

# 44_MainGuardAndStandardLibrary_VehicleClock

**Difficulty:** Medium  
**Primary Python Concept:** Standard-library APIs with a main guard  
**Supporting Concepts:** `datetime`, timezone-aware values, formatting  
**Automotive Domain:** Offline vehicle clock  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Format deterministic timezone-aware timestamps while keeping script execution import-safe.

## Prerequisites
Functions, `datetime`, timezone offsets, format strings, and imports.

## Scenario Introduction
A vehicle clock utility formats a supplied timestamp for an offline service record.

## Problem Statement
**Goal:** Format deterministic timezone-aware timestamps while keeping script execution import-safe.

**Specifically:** Implement `format_vehicle_time(moment: datetime, offset_hours: int) -> str` and a guarded `main()`.

## Task to Implement
Construct the target timezone from the requested offset and use `astimezone` for conversion; return `YYYY-MM-DD HH:MM UTC+/-HH:MM`. Reject naive datetimes and offsets outside -12 through 14. 

## Input Specification
`moment` must be timezone-aware; `offset_hours` is an integer in the inclusive range -12 to 14.

## Output Specification
Return the exact formatted timestamp after applying the offset.

## Rules and Constraints
- Use `datetime` from the standard library.
- Build the target `datetime.timezone` and convert with `moment.astimezone(target_timezone)`; do not add a naive `timedelta` to the wall clock.
- Do not use the current system time in the function.
- The main guard is required.

## Hints
Check `tzinfo` and `utcoffset()` before applying the requested offset.

## Common Mistakes
- Calling `datetime.now()` inside the calculation.
- Confusing source timezone with target offset.
- Omitting the sign from UTC formatting.

## Extension Challenge
Accept a named `zoneinfo.ZoneInfo` region instead of an integer offset.
