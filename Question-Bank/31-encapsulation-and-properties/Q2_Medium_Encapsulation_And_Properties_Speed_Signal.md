# 31 - Encapsulation and Properties Speed Signal - Medium

## Question Details
- **Concept:** Encapsulation and properties
- **Supporting Python concepts:** Read-only properties, validation, derived values
- **Difficulty:** Medium
- **Domain:** Offline speed signal model
- **Learning Objective:** Encapsulate a raw speed value and expose a read-only converted property.
- **Estimated completion time:** 50 minutes

## Scenario
A simulator stores speed in km/h and reports mph without exposing mutable derived state.

## Function Details
Implement class `SpeedSignal` with property `speed_kmh: float` and read-only property `speed_mph: float`.

**Required API / operation:** Create a validated speed object with a read-only mph property.

**Input rules and constraints:** Speed is finite and from 0 through 300 km/h inclusive. Use conversion factor `0.621371`.

**Behavior and return shape:** `speed_kmh` returns a float rounded to one decimal. `speed_mph` returns converted speed rounded to one decimal.

**Implementation rules:** Store km/h in `_speed_kmh`. The mph property must not have a setter. Raise `ValueError` for invalid values.

## Tasks to Implement
1. Encapsulate a raw speed value and expose a read-only converted property.
2. Create a validated speed object with a read-only mph property.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `signal=SpeedSignal(0); (signal.speed_kmh, signal.speed_mph)` | `(0.0, 0.0)` |
| 2 | `signal=SpeedSignal(100); (signal.speed_kmh, signal.speed_mph)` | `(100.0, 62.1)` |
| 3 | `signal=SpeedSignal(300); (signal.speed_kmh, signal.speed_mph)` | `(300.0, 186.4)` |
| 4 | `signal=SpeedSignal(1.25); (signal.speed_kmh, signal.speed_mph)` | `(1.2, 0.8)` |
| 5 | `signal=SpeedSignal(88.5); (signal.speed_kmh, signal.speed_mph)` | `(88.5, 55.0)` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, properties, numeric conversion, and exceptions.

### Rules and Constraints
- Store km/h in `_speed_kmh`.
- The mph property must not have a setter.
- Raise `ValueError` for invalid values.

### Hints
1. Validate km/h in its setter.
2. Calculate mph from the stored km/h.
3. Define only a getter for `speed_mph`.

### Common Mistakes
- Storing two independently mutable speeds.
- Using 0.62 instead of the specified factor.
- Returning an unrounded conversion.

### Extension Challenge
Add a setter for km/h while keeping mph read-only.
