# 26 - Date and Time Handling Charging Sessions - Medium

## Question Details
- **Concept:** Date and time handling
- **Supporting Python concepts:** Time zones, aware datetimes, duration
- **Difficulty:** Medium
- **Domain:** Offline charging-session duration
- **Learning Objective:** Calculate elapsed charging time from timezone-aware ISO timestamps.
- **Estimated completion time:** 50 minutes

## Scenario
A charging simulator records start and end timestamps from a station with explicit UTC offsets.

## Function Details
Implement `charging_duration_minutes(start: str, end: str) -> float`.

**Required API / operation:** Return elapsed minutes between two timestamps, rounded to one decimal place.

**Input rules and constraints:** Inputs are ISO 8601 timestamps with timezone offsets, such as `2026-08-26T10:00:00-04:00`. End must be later than start and duration must be at most 24 hours.

**Behavior and return shape:** Return elapsed minutes rounded to one decimal place, comparing absolute instants.

**Implementation rules:** Require timezone-aware parsed values. Use UTC-aware arithmetic or direct aware subtraction. Raise `ValueError` for malformed, naive, reversed, or overly long sessions.

## Tasks to Implement
1. Calculate elapsed charging time from timezone-aware ISO timestamps.
2. Return elapsed minutes between two timestamps, rounded to one decimal place.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `start="2026-08-26T10:00:00-04:00", end="2026-08-26T11:00:00-04:00"` | `60.0` |
| 2 | `start="2026-08-26T10:00:00-04:00", end="2026-08-26T10:00:30-04:00"` | `0.5` |
| 3 | `start="2026-08-26T10:00:00-04:00", end="2026-08-27T10:00:00-04:00"` | `1440.0` |
| 4 | `start="2026-08-26T10:00:00-04:00", end="2026-08-26T16:00:00Z"` | `120.0` |
| 5 | `start="2026-08-26T00:00:00+02:00", end="2026-08-26T00:30:00+02:00"` | `30.0` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, `datetime`, timezone offsets, and validation.

### Rules and Constraints
- Require timezone-aware parsed values.
- Use UTC-aware arithmetic or direct aware subtraction.
- Raise `ValueError` for malformed, naive, reversed, or overly long sessions.

### Hints
1. Parse with `datetime.fromisoformat`.
2. Check `tzinfo` and `utcoffset`.
3. Convert the timedelta to seconds before dividing by 60.

### Common Mistakes
- Comparing local clock text directly.
- Accepting timestamps without offsets.
- Rounding seconds before calculating minutes.

### Extension Challenge
Return both duration and the UTC-normalized start timestamp.
