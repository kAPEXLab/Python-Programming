# 26_DateAndTimeHandling_ServiceIntervals

**Difficulty:** Easy
**Primary Python Concept:** Date and time handling  
**Supporting Concepts:** `datetime.date`, intervals, ISO formatting  
**Automotive Domain:** Offline maintenance scheduling  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Compute a next service date using calendar-aware date arithmetic.

## Prerequisites
Functions, dates, integers, and validation.

## Scenario Introduction
A service planner schedules the next inspection from the last service date and a fixed interval in days.

## Problem Statement
**Goal:** Compute a next service date using calendar-aware date arithmetic.

**Specifically:** Return the ISO date when the next service is due.

## Task to Implement
Implement `next_service_date(last_service: str, interval_days: int) -> str`.

## Input Specification
`last_service` is an ISO calendar date. `interval_days` is an integer from 1 through 730 inclusive.

## Output Specification
Return the next date as `YYYY-MM-DD`.

## Rules and Constraints
- Use `datetime.date` and `timedelta`.
- Reject booleans, invalid dates, and out-of-range intervals with `ValueError`.
- The calculation is independent of the current clock.

## Hints
1. Parse with `date.fromisoformat`.
2. Add `timedelta(days=interval_days)`.
3. Return `isoformat()`.

## Common Mistakes
- Assuming every month has 30 days.
- Using the current date in the result.
- Accepting a boolean as an integer interval.

## Extension Challenge
Support a list of blackout dates and move the result to the next available weekday.
