# 26_DateAndTimeHandling_FleetTrips

**Difficulty:** Difficult
**Primary Python Concept:** Date and time handling  
**Supporting Concepts:** Date grouping, weekday logic, records  
**Automotive Domain:** Offline fleet trip calendar summary  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Group trip records by calendar date using parsed timestamps.

## Prerequisites
Datetimes, lists of dictionaries, loops, and validation.

## Scenario Introduction
A fleet report contains trips with UTC timestamps and distance values.

## Problem Statement
**Goal:** Group trip records by calendar date using parsed timestamps.

**Specifically:** Summarize total kilometers by UTC calendar date.

## Task to Implement
Implement `daily_fleet_distance(trips: list[dict[str, object]]) -> dict[str, float]`.

## Input Specification
Each trip has `started_at` as an ISO timestamp with `Z` or `+00:00`, and `distance_km` as a finite number from 0 through 5000. Empty input is allowed.

## Output Specification
Return ISO date keys sorted lexicographically and distances rounded to one decimal place.

## Rules and Constraints
- Interpret all timestamps in UTC.
- Reject malformed records, extra keys, naive timestamps, or negative distances.
- Do not mutate trip records.

## Hints
1. Normalize `Z` to a parseable UTC offset if needed.
2. Convert each timestamp to UTC before taking `.date()`.
3. Accumulate in insertion order, then round values.

## Common Mistakes
- Grouping by local date before converting to UTC.
- Treating an empty list as an error.
- Rounding each trip before summing.

## Extension Challenge
Add trip counts beside each daily distance.
