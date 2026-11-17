# 19 - Arguments Returns and Scope Battery Summary - Difficult

## Question Details
- **Concept:** Argument passing and scope isolation
- **Supporting Python concepts:** Nested functions, closures, validation, rounding
- **Difficulty:** Difficult
- **Domain:** Simulated battery summary
- **Learning Objective:** Use a local helper function to summarize battery readings without leaking state between calls.
- **Estimated completion time:** 50 minutes

## Scenario
An offline battery fixture contains voltage and temperature samples paired by index.

## Function Details
Implement `battery_summary(readings: list[tuple[float, float]], *, minimum_voltage: float = 11.5) -> dict[str, object]`.

**Required API / operation:** Return voltage average, maximum temperature, and a health label based on local thresholds.

**Input rules and constraints:** Each pair is `(voltage, temperature_c)` with voltage 0.0 through 20.0 and temperature -40.0 through 120.0. Minimum voltage is 0.0 through 20.0. The list has 1 through 500 items.

**Behavior and return shape:** Return `average_voltage` rounded to two decimals, `max_temperature_c` rounded to one decimal, and `health`: `"HEALTHY"` if every voltage is at least the threshold and maximum temperature is at most 60.0, otherwise `"CHECK"`.

**Implementation rules:** Define any normalization helper inside the function so it cannot retain cross-call state. Reject malformed data with `ValueError`. Keep the input unchanged.

## Tasks to Implement
1. Use a local helper function to summarize battery readings without leaking state between calls.
2. Return voltage average, maximum temperature, and a health label based on local thresholds.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `readings=[(12.0, 25.0)]` | `{'average_voltage': 12.0, 'max_temperature_c': 25.0, 'health': 'HEALTHY'}` |
| 2 | `readings=[(11.5, 60.0)]` | `{'average_voltage': 11.5, 'max_temperature_c': 60.0, 'health': 'HEALTHY'}` |
| 3 | `readings=[(11.4, 20.0)]` | `{'average_voltage': 11.4, 'max_temperature_c': 20.0, 'health': 'CHECK'}` |
| 4 | `readings=[(12.0, 60.1)]` | `{'average_voltage': 12.0, 'max_temperature_c': 60.1, 'health': 'CHECK'}` |
| 5 | `readings=[(12.0, 40.0), (13.0, 55.54)]` | `{'average_voltage': 12.5, 'max_temperature_c': 55.5, 'health': 'HEALTHY'}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, local scope, closures, lists, arithmetic, and validation.

### Rules and Constraints
- Define any normalization helper inside the function so it cannot retain cross-call state.
- Reject malformed data with `ValueError`.
- Keep the input unchanged.

### Hints
1. Validate the threshold separately from readings.
2. Use a local helper for normalized reading access if useful.
3. Health uses every voltage and the maximum temperature.

### Common Mistakes
- Letting a previous call affect the next result.
- Using average temperature instead of maximum.
- Treating threshold equality as failure.

### Extension Challenge
Return the index of the first reading that violates a health condition.
