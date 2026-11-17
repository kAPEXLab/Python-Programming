# 26 - Date and Time Handling Fleet Trips - Difficult

## Question Details
- **Concept:** Date and time handling
- **Supporting Python concepts:** Date grouping, weekday logic, records
- **Difficulty:** Difficult
- **Domain:** Offline fleet trip calendar summary
- **Learning Objective:** Group trip records by calendar date using parsed timestamps.
- **Estimated completion time:** 50 minutes

## Scenario
A fleet report contains trips with UTC timestamps and distance values.

## Function Details
Implement `daily_fleet_distance(trips: list[dict[str, object]]) -> dict[str, float]`.

**Required API / operation:** Summarize total kilometers by UTC calendar date.

**Input rules and constraints:** Each trip has `started_at` as an ISO timestamp with `Z` or `+00:00`, and `distance_km` as a finite number from 0 through 5000. Empty input is allowed.

**Behavior and return shape:** Return ISO date keys sorted lexicographically and distances rounded to one decimal place.

**Implementation rules:** Interpret all timestamps in UTC. Reject malformed records, extra keys, naive timestamps, or negative distances. Do not mutate trip records.

## Tasks to Implement
1. Group trip records by calendar date using parsed timestamps.
2. Summarize total kilometers by UTC calendar date.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `trips=[]` | `{}` |
| 2 | `trips=[{"started_at":"2026-08-26T10:00:00Z","distance_km":12.34}]` | `{'2026-08-26': 12.3}` |
| 3 | `trips=[{"started_at":"2026-08-26T23:30:00Z","distance_km":10},{"started_at":"2026-08-27T01:00:00+00:00","distance_km":5}]` | `{'2026-08-26': 10.0, '2026-08-27': 5.0}` |
| 4 | `trips=[{"started_at":"2026-08-26T10:00:00Z","distance_km":1.25},{"started_at":"2026-08-26T12:00:00Z","distance_km":2.25}]` | `{'2026-08-26': 3.5}` |
| 5 | `trips=[{"started_at":"2026-01-01T00:30:00Z","distance_km":0},{"started_at":"2025-12-31T23:30:00+00:00","distance_km":5000}]` | `{'2025-12-31': 5000.0, '2026-01-01': 0.0}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Datetimes, lists of dictionaries, loops, and validation.

### Rules and Constraints
- Interpret all timestamps in UTC.
- Reject malformed records, extra keys, naive timestamps, or negative distances.
- Do not mutate trip records.

### Hints
1. Normalize `Z` to a parseable UTC offset if needed.
2. Convert each timestamp to UTC before taking `.date()`.
3. Accumulate in insertion order, then round values.

### Common Mistakes
- Grouping by local date before converting to UTC.
- Treating an empty list as an error.
- Rounding each trip before summing.

### Extension Challenge
Add trip counts beside each daily distance.
