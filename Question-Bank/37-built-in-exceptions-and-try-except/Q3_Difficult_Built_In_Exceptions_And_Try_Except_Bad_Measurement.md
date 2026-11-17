# 37 - Summarizing Fuel Economy Measurements - Difficult

## Question Details
- **Concept:** Built-in exceptions and try-except
- **Supporting Python concepts:** Numeric conversion, `ZeroDivisionError`, validation, aggregation
- **Difficulty:** Difficult
- **Domain:** Offline fuel-economy measurement
- **Learning Objective:** Handle malformed and unusable measurements while calculating a useful summary.

## Scenario
A test report receives distance and fuel pairs, some of which cannot produce a valid economy value.

## Function Details
- **Required Python interface:** Implement `summarize_economy(measurements: list[tuple[object, object]]) -> tuple[list[float], int]`.
- **Behavior:** Convert distance and liters to floats, calculate km per liter, and round valid results to two decimals. Count entries with conversion errors, zero fuel, or negative values as rejected.
- **Return shape:** Return valid economy values and the number rejected, preserving valid order.
- **Input rules and constraints:** Pairs are `(distance_km, liters)`. The list may be empty. Valid values are non-negative distance and strictly positive fuel. Additional constraints: Handle `ValueError`, `TypeError`, and `ZeroDivisionError` deliberately; Do not treat a rejected measurement as zero; No real fuel-system data is used.

## Tasks to Implement
1. Implement the specified Python interface: Implement `summarize_economy(measurements: list[tuple[object, object]]) -> tuple[list[float], int]`.
2. Apply the stated input validation and constraints: Pairs are `(distance_km, liters)`. The list may be empty. Valid values are non-negative distance and strictly positive fuel.
3. Implement the required behavior: Convert distance and liters to floats, calculate km per liter, and round valid results to two decimals. Count entries with conversion errors, zero fuel, or negative values as rejected.
4. Return the specified result shape without changing the required ordering or formatting: Return valid economy values and the number rejected, preserving valid order.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `summarize_economy([(100, 5), (90, 3)])` | `([20.0, 30.0], 0)` |
| 2 | `summarize_economy([])` | `([], 0)` |
| 3 | `summarize_economy([(0, 2)])` | `([0.0], 0)` |
| 4 | `summarize_economy([(100, 0), (50, 2)])` | `([25.0], 1)` |
| 5 | `summarize_economy([("bad", 1), (12, 0.5)])` | `([24.0], 1)` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Functions, lists, numeric conversion, loops, and exception handling.

### Rules and Constraints

- Handle `ValueError`, `TypeError`, and `ZeroDivisionError` deliberately.
- Do not treat a rejected measurement as zero.
- No real fuel-system data is used.

### Hints

Convert each field inside the loop and calculate only after validation.

### Common Mistakes

- Catching division errors after performing invalid arithmetic.
- Counting valid zero-distance records as errors.
- Stopping at the first malformed pair.

### Extension Challenge

Return rejected indexes and a reason for each.
