# 01 - Telemetry Report - Medium

## Question Details
- Concept: Python syntax and program structure
- Supporting concepts: Functions, lists, loops, conditionals, formatted output
- Difficulty: Medium
- Domain: Vehicle telemetry
- Learning Objective: Count threshold-crossing telemetry readings and format their average speed.

## Scenario
Structure a multi‑step Python program that processes telemetry records and returns a deterministic report. Each simulated record contains a timestamp (seconds) and vehicle speed (km/h). The function must count how many readings are at or above a configurable speed limit and calculate the average speed.

## Function Details
- Function signature: `summarize_telemetry(readings: list[tuple[int, int | float]], speed_limit: int | float) -> str`
- Behavior / return shape: Count telemetry speeds at or above the configurable speed limit, calculate the mean speed (or 0.00 for no readings), and format the three-line report.
- Exact accepted inputs: `readings` is a list of two-item tuples. Each timestamp is an integer greater than or equal to 0; each speed is a finite `int` or `float` from 0 through 300 km/h. `speed_limit` is a finite `int` or `float` from 0 through 300. Reject booleans, malformed tuples, invalid values, or any out-of-range value with `ValueError`. Empty `readings` is valid; do not mutate the input.
- Output and validation / behavior: Return exactly three lines: `Readings: N`, `Average speed: X.XX km/h`, and `Over limit: M`. Use `0.00` for the empty-list average; count speeds greater than or equal to `speed_limit`.

## Tasks to Implement
1. Implement `summarize_telemetry` with the exact signature above. Validate that `readings` is a list of two-item tuples, each timestamp is a non-negative integer, and each speed and `speed_limit` is a finite, non-boolean number from 0 through 300. Raise `ValueError` for malformed or out-of-range values. Allow an empty list and do not mutate the input.
2. Count telemetry speeds at or above the configurable speed limit, calculate the mean speed (or 0.00 for no readings), and format the three-line report.
3. Implement this output contract exactly: Return exactly three lines: Readings: N, Average speed: X.XX km/h, and Over limit: M. Use 0.00 for the empty-list average; count speeds greater than or equal to speed_limit.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | summarize_telemetry([(0, 50), (1, 90)], 80) | Readings: 2<br>Average speed: 70.00 km/h<br>Over limit: 1 | Typical valid input using the specified tuple record shape. |
| 2 | summarize_telemetry([], 0) | Readings: 0<br>Average speed: 0.00 km/h<br>Over limit: 0 | Valid boundary or threshold case. |
| 3 | summarize_telemetry([(5, 100)], 100) | Readings: 1<br>Average speed: 100.00 km/h<br>Over limit: 1 | Confirms readings exactly at the speed limit are counted. |
| 4 | summarize_telemetry([(1, 0), (2, 300)], 200) | Readings: 2<br>Average speed: 150.00 km/h<br>Over limit: 1 | Exercises the minimum and maximum accepted speed values. |
| 5 | summarize_telemetry([(0, 80), (4, 80)], 80) | Readings: 2<br>Average speed: 80.00 km/h<br>Over limit: 2 | Confirms each reading equal to the limit is counted. |

## Expected Deliverables
- Complete implementation of the required function that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.
