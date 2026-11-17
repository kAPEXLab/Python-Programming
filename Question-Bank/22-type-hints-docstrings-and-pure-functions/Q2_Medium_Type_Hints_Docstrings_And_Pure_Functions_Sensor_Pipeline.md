# 22 - Type Hints Docstrings and Pure Functions Sensor Pipeline - Medium

## Question Details
- **Concept:** Type hints, docstrings, and pure functions
- **Supporting Python concepts:** Lists, filtering, averages, validation
- **Difficulty:** Medium
- **Domain:** Offline sensor-data cleanup
- **Learning Objective:** Build a typed pure function that filters valid sensor readings and returns a deterministic summary.
- **Estimated completion time:** 40 minutes

## Scenario
A simulated temperature pipeline receives a batch of Celsius readings. Only the sentinel value `-999.0` is ignored; every other out-of-range value raises `ValueError`.

## Function Details
Implement `summarize_temperatures(readings: list[float]) -> tuple[int, float]` with a docstring.

**Required API / operation:** Return the count and average of valid readings in a tuple.

**Input rules and constraints:** Readings must be a list of finite numbers. Only `-999.0` is ignored as an unavailable sample; every other value outside -40.0 through 150.0 C raises `ValueError`.

**Behavior and return shape:** Return `(valid_count, average_celsius)`. The average is rounded to two decimals. Raise `ValueError` if the list is empty or contains no valid samples.

**Implementation rules:** Do not mutate the input list. Treat only `-999.0` as an unavailable sentinel. Include complete parameter and return type annotations.

## Tasks to Implement
1. Build a typed pure function that filters valid sensor readings and returns a deterministic summary.
2. Return the count and average of valid readings in a tuple.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `readings=[-999.0, 20.0]` | `(1, 20.0)` |
| 2 | `readings=[0.0, 10.0, 20.0]` | `(3, 10.0)` |
| 3 | `readings=[-40.0, 150.0]` | `(2, 55.0)` |
| 4 | `readings=[-999.0, -40.0, 150.0]` | `(2, 55.0)` |
| 5 | `readings=[21.124, 22.128]` | `(2, 21.63)` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, lists, loops or comprehensions, floats, and exceptions.

### Rules and Constraints
- Do not mutate the input list.
- Treat only `-999.0` as an unavailable sentinel.
- Include complete parameter and return type annotations.

### Hints
1. Build a new collection of non-sentinel values.
2. Check the filtered collection before dividing.
3. Round only the final average.

### Common Mistakes
- Including `-999.0` in the average.
- Sorting or modifying the caller's list unnecessarily.
- Returning the raw unrounded average.

### Extension Challenge
Return minimum and maximum values in a typed named tuple without changing the original function.
