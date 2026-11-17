# 18 - Function Definition and Parameters Range Estimator - Medium

## Question Details
- **Concept:** Multiple parameters and defaults
- **Supporting Python concepts:** Arithmetic, validation, rounding, functions
- **Difficulty:** Medium
- **Domain:** Simulated EV range estimation
- **Learning Objective:** Define a function with multiple parameters and a default reserve percentage.

## Scenario
A fleet telemetry system is estimating how far an EV can travel after reserving a safety buffer of battery energy for unexpected traffic or charging delays. The calculation must use the battery capacity that remains after the reserve is removed, then convert the usable energy into a realistic driving range in kilometers.

## Function Details
Implement `estimate_range(energy_kwh: float, consumption_kwh_per_100km: float, reserve_percent: float = 10.0) -> float`.

**Required API / operation:** Estimate drivable range while reserving a configurable percentage of energy.

**Input rules and constraints:** Energy is 1.0 through 200.0 kWh, consumption is 5.0 through 50.0 kWh/100 km, and reserve is 0.0 through 50.0 percent. Values are finite and non-boolean.

**Behavior and return shape:** Return `((energy_kwh * (1 - reserve_percent / 100)) / consumption_kwh_per_100km) * 100`, rounded to one decimal km.

**Implementation rules:** The default reserve is exactly 10.0 percent. Validate every parameter and do not mutate anything. Raise `ValueError` for invalid values.

## Tasks to Implement
1. Define a function with multiple parameters and a default reserve percentage.
2. Estimate drivable range while reserving a configurable percentage of energy.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `energy_kwh=50, consumption_kwh_per_100km=10 (default reserve)` | `450.0` |
| 2 | `energy_kwh=1, consumption_kwh_per_100km=5, reserve_percent=0` | `20.0` |
| 3 | `energy_kwh=200, consumption_kwh_per_100km=5, reserve_percent=50` | `2000.0` |
| 4 | `energy_kwh=100, consumption_kwh_per_100km=20, reserve_percent=25` | `375.0` |
| 5 | `energy_kwh=10, consumption_kwh_per_100km=5, reserve_percent=50` | `100.0` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Function parameters, arithmetic, floats, validation, and return values.

### Rules and Constraints
- The default reserve is exactly 10.0 percent.
- Validate every parameter and do not mutate anything.
- Raise `ValueError` for invalid values.

### Hints
1. Convert reserve percent to a fraction.
2. Apply the reserve before dividing by consumption.
3. Round the final distance only.

### Common Mistakes
- Subtracting 10 kWh instead of 10 percent.
- Applying reserve after calculating distance.
- Forgetting the factor of 100 for km.

### Extension Challenge
Add an optional ambient-temperature efficiency factor with a documented range.
