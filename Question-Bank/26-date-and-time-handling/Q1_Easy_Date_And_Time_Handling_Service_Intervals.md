# 26 - Date and Time Handling Service Intervals - Easy

## Question Details
- **Concept:** Date and time handling
- **Supporting Python concepts:** `datetime.date`, intervals, ISO formatting
- **Difficulty:** Easy
- **Domain:** Offline maintenance scheduling
- **Learning Objective:** Compute a next service date using calendar-aware date arithmetic.
- **Estimated completion time:** 45 minutes

## Scenario
A service planner schedules the next inspection from the last service date and a fixed interval in days.

## Function Details
Implement `next_service_date(last_service: str, interval_days: int) -> str`.

**Required API / operation:** Return the ISO date when the next service is due.

**Input rules and constraints:** `last_service` is an ISO calendar date. `interval_days` is an integer from 1 through 730 inclusive.

**Behavior and return shape:** Return the next date as `YYYY-MM-DD`.

**Implementation rules:** Use `datetime.date` and `timedelta`. Reject booleans, invalid dates, and out-of-range intervals with `ValueError`. The calculation is independent of the current clock.

## Tasks to Implement
1. Compute a next service date using calendar-aware date arithmetic.
2. Return the ISO date when the next service is due.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `last_service="2024-01-01", interval_days=1` | `'2024-01-02'` |
| 2 | `last_service="2024-02-28", interval_days=1` | `'2024-02-29'` |
| 3 | `last_service="2024-02-29", interval_days=1` | `'2024-03-01'` |
| 4 | `last_service="2023-12-31", interval_days=1` | `'2024-01-01'` |
| 5 | `last_service="2025-01-01", interval_days=730` | `'2027-01-01'` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, dates, integers, and validation.

### Rules and Constraints
- Use `datetime.date` and `timedelta`.
- Reject booleans, invalid dates, and out-of-range intervals with `ValueError`.
- The calculation is independent of the current clock.

### Hints
1. Parse with `date.fromisoformat`.
2. Add `timedelta(days=interval_days)`.
3. Return `isoformat()`.

### Common Mistakes
- Assuming every month has 30 days.
- Using the current date in the result.
- Accepting a boolean as an integer interval.

### Extension Challenge
Support a list of blackout dates and move the result to the next available weekday.
