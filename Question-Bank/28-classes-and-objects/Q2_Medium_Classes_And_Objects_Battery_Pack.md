# 28 - Classes and Objects Battery Pack - Medium

## Question Details
- **Concept:** Classes and objects
- **Supporting Python concepts:** State, calculations, validation
- **Difficulty:** Medium
- **Domain:** Offline battery-pack model
- **Learning Objective:** Represent battery state as an object and expose a calculated energy value.
- **Estimated completion time:** 50 minutes

## Scenario
A simulator tracks nominal battery capacity and state of charge for one pack.

## Function Details
Implement class `BatteryPack` with `capacity_kwh: float`, `soc_percent: float`, and method `stored_energy_kwh(self) -> float`.

**Required API / operation:** Create a battery object that calculates currently stored energy.

**Input rules and constraints:** Capacity is greater than 0 and at most 500 kWh. SOC is from 0 through 100 inclusive. Values must be finite numbers.

**Behavior and return shape:** Return capacity times SOC divided by 100, rounded to two decimals.

**Implementation rules:** Store the two values on each instance. Raise `ValueError` for invalid construction. This is a static model, not a battery-management interface.

## Tasks to Implement
1. Represent battery state as an object and expose a calculated energy value.
2. Create a battery object that calculates currently stored energy.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `BatteryPack(1, 0).stored_energy_kwh()` | `0.0` |
| 2 | `BatteryPack(100, 50).stored_energy_kwh()` | `50.0` |
| 3 | `BatteryPack(500, 100).stored_energy_kwh()` | `500.0` |
| 4 | `BatteryPack(75.5, 80).stored_energy_kwh()` | `60.4` |
| 5 | `BatteryPack(1, 12.345).stored_energy_kwh()` | `0.12` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, floats, methods, and exceptions.

### Rules and Constraints
- Store the two values on each instance.
- Raise `ValueError` for invalid construction.
- This is a static model, not a battery-management interface.

### Hints
1. Validate ranges in the constructor.
2. Keep SOC as a percentage, not a fraction.
3. Round the method result only at return time.

### Common Mistakes
- Dividing SOC by 10 instead of 100.
- Allowing negative capacity.
- Making capacity a shared class attribute.

### Extension Challenge
Add a method for usable energy after a fixed 5% reserve.
