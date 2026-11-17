# 44 - Formatting Vehicle Clock Timestamps - Medium

## Question Details
- **Concept:** Standard-library APIs with a main guard
- **Supporting Python concepts:** `datetime`, timezone-aware values, formatting
- **Difficulty:** Medium
- **Domain:** Offline vehicle clock
- **Learning Objective:** Format deterministic timezone-aware timestamps while keeping script execution import-safe.

## Scenario
A vehicle clock utility formats a supplied timestamp for an offline service record.

## Function Details
- **Required Python interface:** Implement `format_vehicle_time(moment: datetime, offset_hours: int) -> str` and a guarded `main()`.
- **Behavior:** Construct the target timezone from the requested offset and use `astimezone` for conversion; return `YYYY-MM-DD HH:MM UTC+/-HH:MM`. Reject naive datetimes and offsets outside -12 through 14.
- **Return shape:** Return the exact formatted timestamp after applying the offset.
- **Input rules and constraints:** `moment` must be timezone-aware; `offset_hours` is an integer in the inclusive range -12 to 14. Additional constraints: Use `datetime` from the standard library; Build the target `datetime.timezone` and convert with `moment.astimezone(target_timezone)`; do not add a naive `timedelta` to the wall clock; Do not use the current system time in the function; The main guard is required.

## Tasks to Implement
1. Implement the specified Python interface: Implement `format_vehicle_time(moment: datetime, offset_hours: int) -> str` and a guarded `main()`.
2. Apply the stated input validation and constraints: `moment` must be timezone-aware; `offset_hours` is an integer in the inclusive range -12 to 14.
3. Implement the required behavior: Construct the target timezone from the requested offset and use `astimezone` for conversion; return `YYYY-MM-DD HH:MM UTC+/-HH:MM`. Reject naive datetimes and offsets outside -12 through 14.
4. Return the specified result shape without changing the required ordering or formatting: Return the exact formatted timestamp after applying the offset.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `format_vehicle_time(datetime(2024, 1, 1, 10, 0, tzinfo=timezone.utc), 0)` | `"2024-01-01 10:00 UTC+00:00"` |
| 2 | `format_vehicle_time(datetime(2024, 1, 1, 10, 0, tzinfo=timezone.utc), -5)` | `"2024-01-01 05:00 UTC-05:00"` |
| 3 | `format_vehicle_time(datetime(2024, 1, 1, 10, 0, tzinfo=timezone.utc), 5)` | `"2024-01-01 15:00 UTC+05:00"` |
| 4 | `format_vehicle_time(datetime(2024, 6, 15, 23, 30, tzinfo=timezone.utc), 14)` | `"2024-06-16 13:30 UTC+14:00"` |
| 5 | `format_vehicle_time(datetime(2024, 6, 15, 0, 30, tzinfo=timezone.utc), -12)` | `"2024-06-14 12:30 UTC-12:00"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Functions, `datetime`, timezone offsets, format strings, and imports.

### Rules and Constraints

- Use `datetime` from the standard library.
- Build the target `datetime.timezone` and convert with `moment.astimezone(target_timezone)`; do not add a naive `timedelta` to the wall clock.
- Do not use the current system time in the function.
- The main guard is required.

### Hints

Check `tzinfo` and `utcoffset()` before applying the requested offset.

### Common Mistakes

- Calling `datetime.now()` inside the calculation.
- Confusing source timezone with target offset.
- Omitting the sign from UTC formatting.

### Extension Challenge

Accept a named `zoneinfo.ZoneInfo` region instead of an integer offset.
