# 26_DateAndTimeHandling_ChargingSessions

**Difficulty:** Medium
**Primary Python Concept:** Date and time handling  
**Supporting Concepts:** Time zones, aware datetimes, duration  
**Automotive Domain:** Offline charging-session duration  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Calculate elapsed charging time from timezone-aware ISO timestamps.

## Prerequisites
Functions, `datetime`, timezone offsets, and validation.

## Scenario Introduction
A charging simulator records start and end timestamps from a station with explicit UTC offsets.

## Problem Statement
**Goal:** Calculate elapsed charging time from timezone-aware ISO timestamps.

**Specifically:** Return elapsed minutes between two timestamps, rounded to one decimal place.

## Task to Implement
Implement `charging_duration_minutes(start: str, end: str) -> float`.

## Input Specification
Inputs are ISO 8601 timestamps with timezone offsets, such as `2026-08-26T10:00:00-04:00`. End must be later than start and duration must be at most 24 hours.

## Output Specification
Return elapsed minutes rounded to one decimal place, comparing absolute instants.

## Rules and Constraints
- Require timezone-aware parsed values.
- Use UTC-aware arithmetic or direct aware subtraction.
- Raise `ValueError` for malformed, naive, reversed, or overly long sessions.

## Hints
1. Parse with `datetime.fromisoformat`.
2. Check `tzinfo` and `utcoffset`.
3. Convert the timedelta to seconds before dividing by 60.

## Common Mistakes
- Comparing local clock text directly.
- Accepting timestamps without offsets.
- Rounding seconds before calculating minutes.

## Extension Challenge
Return both duration and the UTC-normalized start timestamp.
