# 36 - Battery Capacity Arithmetic - Medium

## Question Details
- **Concept:** Operator overloading
- **Supporting Python concepts:** Value objects, reflected operators, clamping, type checks
- **Difficulty:** Medium
- **Domain:** Offline battery capacity accounting
- **Learning Objective:** Overload arithmetic for a capacity type while enforcing physical bounds.

## Scenario
A simulator models charge added to or consumed from a battery pack.

## Function Details
- **Required Python interface:** Implement `BatteryCapacity(kwh: float, maximum_kwh: float)` with `__add__`, `__sub__`, `__rsub__`, and `percent()`.
- **Behavior:** The maximum must be positive and current capacity must be from 0 through maximum. Addition and subtraction use another `BatteryCapacity` with the same maximum and reject results outside bounds. `percent()` returns a percentage rounded to one decimal.
- **Return shape:** Arithmetic returns a new capacity with the same maximum; percent returns a float.
- **Input rules and constraints:** All capacities are finite. Maximum capacity is 1 through 2000 kWh. Additional constraints: Preserve the maximum in results; Reject mismatched maximum capacities with `ValueError`; Do not connect to a real battery.

## Tasks to Implement
1. Implement the specified Python interface: Implement `BatteryCapacity(kwh: float, maximum_kwh: float)` with `__add__`, `__sub__`, `__rsub__`, and `percent()`.
2. Apply the stated input validation and constraints: All capacities are finite. Maximum capacity is 1 through 2000 kWh.
3. Implement the required behavior: The maximum must be positive and current capacity must be from 0 through maximum. Addition and subtraction use another `BatteryCapacity` with the same maximum and reject results outside bounds. `percent()` returns a percentage rounded to one decimal.
4. Return the specified result shape without changing the required ordering or formatting: Arithmetic returns a new capacity with the same maximum; percent returns a float.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `(BatteryCapacity(25.0, 100.0) + BatteryCapacity(10.0, 100.0)).kwh` | `35.0` |
| 2 | `(BatteryCapacity(75.0, 100.0) - BatteryCapacity(25.0, 100.0)).kwh` | `50.0` |
| 3 | `(BatteryCapacity(100.0, 100.0) - BatteryCapacity(20.0, 100.0)).kwh` | `80.0` |
| 4 | `BatteryCapacity(33.3, 100.0).percent()` | `33.3` |
| 5 | `(BatteryCapacity(40.0, 80.0) + BatteryCapacity(10.0, 80.0)).percent()` | `62.5` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Classes, special methods, arithmetic, and validation.

### Rules and Constraints

- Preserve the maximum in results.
- Reject mismatched maximum capacities with `ValueError`.
- Do not connect to a real battery.

### Hints

Check maximum capacities before calculating the new current value.

### Common Mistakes

- Clamping silently instead of rejecting invalid arithmetic.
- Comparing only current capacity.
- Returning a raw float from addition.

### Extension Challenge

Implement `__repr__` with an exact constructor-like format.
