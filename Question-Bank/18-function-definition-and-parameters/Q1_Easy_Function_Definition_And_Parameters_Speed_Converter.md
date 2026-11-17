# 18 - Function Definition and Parameters Speed Converter - Easy

## Question Details
- **Concept:** Function definitions and parameters
- **Supporting Python concepts:** Arithmetic, type validation, rounding, return values
- **Difficulty:** Easy
- **Domain:** Speed unit conversion
- **Learning Objective:** Define a function with a typed parameter and return a rounded converted value.
- **Estimated completion time:** 25 minutes

## Scenario
An offline dashboard needs to display a speed in miles per hour from kilometers per hour.

## Function Details
Implement `kmh_to_mph(speed_kmh: float) -> float`.

**Required API / operation:** Convert one valid speed without changing the original unit value.

**Input rules and constraints:** Speed is a finite number from 0.0 through 240.0 km/h. Use `1 km/h = 0.621371 mph`.

**Behavior and return shape:** Return `speed_kmh * 0.621371`, rounded to two decimal places.

**Implementation rules:** Use the given conversion factor exactly. Reject booleans, non-numeric, non-finite, or out-of-range inputs with `ValueError`. Return a new numeric result.

## Tasks to Implement
1. Define a function with a typed parameter and return a rounded converted value.
2. Convert one valid speed without changing the original unit value.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `speed_kmh=0.0` | `0.0` |
| 2 | `speed_kmh=1.0` | `0.62` |
| 3 | `speed_kmh=100.0` | `62.14` |
| 4 | `speed_kmh=240.0` | `149.13` |
| 5 | `speed_kmh=10.5` | `6.52` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, numbers, operators, and exceptions.

### Rules and Constraints
- Use the given conversion factor exactly.
- Reject booleans, non-numeric, non-finite, or out-of-range inputs with `ValueError`.
- Return a new numeric result.

### Hints
1. Validate before multiplying.
2. Use the exact factor from the statement.
3. Round only the returned result.

### Common Mistakes
- Using 0.62 as the factor.
- Rounding before multiplication.
- Accepting negative values.

### Extension Challenge
Add a reverse conversion function with the same validation policy.
