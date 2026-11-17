# 31 - Encapsulation and Properties Battery State - Easy

## Question Details
- **Concept:** Encapsulation and properties
- **Supporting Python concepts:** Private attributes, setters, invariants
- **Difficulty:** Easy
- **Domain:** Offline battery state model
- **Learning Objective:** Protect an internal SOC value behind a property that enforces its invariant.
- **Estimated completion time:** 55 minutes

## Scenario
A simulator must prevent state-of-charge values outside the physical percentage range.

## Function Details
Implement class `BatteryState` with property `soc_percent: float` and setter accepting values from 0 through 100.

**Required API / operation:** Expose `soc_percent` as a property while storing the value privately.

**Input rules and constraints:** The constructor accepts `soc_percent: float`; values must be finite numbers, excluding booleans, in the inclusive range 0 to 100.

**Behavior and return shape:** Reading the property returns a float rounded to one decimal. Assignment updates it only after validation.

**Implementation rules:** Store the backing value in `_soc_percent`. Raise `ValueError` for invalid construction or assignment. Do not silently clamp values.

## Tasks to Implement
1. Protect an internal SOC value behind a property that enforces its invariant.
2. Expose `soc_percent` as a property while storing the value privately.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `state=BatteryState(0); state.soc_percent` | `0.0` |
| 2 | `state=BatteryState(100); state.soc_percent` | `100.0` |
| 3 | `state=BatteryState(55.55); state.soc_percent` | `55.5` |
| 4 | `state=BatteryState(20); state.soc_percent=30.25; state.soc_percent` | `30.2` |
| 5 | `state=BatteryState(99.96); state.soc_percent` | `100.0` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, properties, getters, setters, and exceptions.

### Rules and Constraints
- Store the backing value in `_soc_percent`.
- Raise `ValueError` for invalid construction or assignment.
- Do not silently clamp values.

### Hints
1. Put validation in the setter so construction reuses it.
2. Use `math.isfinite` after numeric type checking.
3. Round when reading, not when storing.

### Common Mistakes
- Exposing `_soc_percent` directly as the public API.
- Clamping 100.1 to 100.
- Forgetting that `bool` subclasses `int`.

### Extension Challenge
Add a read-only `is_low` property that is true below 20%.
