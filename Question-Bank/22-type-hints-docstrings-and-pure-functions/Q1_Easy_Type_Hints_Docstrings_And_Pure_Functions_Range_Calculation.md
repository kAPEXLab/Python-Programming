# 22 - Type Hints Docstrings and Pure Functions Range Calculation - Easy

## Question Details
- **Concept:** Type hints, docstrings, and pure functions
- **Supporting Python concepts:** Numeric validation, rounding, return values
- **Difficulty:** Easy
- **Domain:** Offline electric-vehicle range estimation
- **Learning Objective:** Write a documented, type-annotated pure function whose result depends only on its inputs.
- **Estimated completion time:** 35 minutes

## Scenario
A planning tool estimates how far an electric vehicle can travel from usable battery energy and average consumption. The calculation is offline and uses no vehicle connection.

## Function Details
Implement `estimate_range(usable_kwh: float, consumption_kwh_per_100km: float) -> float` with a docstring.

**Required API / operation:** Calculate estimated range from battery energy and energy consumption per 100 km.

**Input rules and constraints:** Both values are finite numbers. Usable energy is from 0 through 200 kWh. Consumption is greater than 0 and at most 100 kWh per 100 km.

**Behavior and return shape:** Return range in km rounded to one decimal place using standard Python `round` behavior.

**Implementation rules:** Keep the function pure: do not read input, print, or modify global state. Reject invalid values with `ValueError`. Include parameter and return annotations and a useful docstring.

## Tasks to Implement
1. Write a documented, type-annotated pure function whose result depends only on its inputs.
2. Calculate estimated range from battery energy and energy consumption per 100 km.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `usable_kwh=0, consumption_kwh_per_100km=1` | `0.0` |
| 2 | `usable_kwh=50, consumption_kwh_per_100km=10` | `500.0` |
| 3 | `usable_kwh=1, consumption_kwh_per_100km=3` | `33.3` |
| 4 | `usable_kwh=200, consumption_kwh_per_100km=100` | `200.0` |
| 5 | `usable_kwh=12.5, consumption_kwh_per_100km=7.5` | `166.7` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, floats, conditionals, and basic exception handling.

### Rules and Constraints
- Keep the function pure: do not read input, print, or modify global state.
- Reject invalid values with `ValueError`.
- Include parameter and return annotations and a useful docstring.

### Hints
1. Divide usable energy by consumption and multiply by 100.
2. Validate before calculating.
3. Use the return annotation exactly as specified.

### Common Mistakes
- Returning a string instead of a float.
- Rounding the inputs before the calculation.
- Depending on a global battery value.

### Extension Challenge
Add a pure function that applies a fixed 10% winter reserve before calling the estimator.
