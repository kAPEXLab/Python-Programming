# 43 - Creating a Reusable Vehicle Utility Module - Easy

## Question Details
- **Concept:** Defining and importing a module
- **Supporting Python concepts:** Public functions, imports, type hints
- **Difficulty:** Easy
- **Domain:** Offline vehicle utility library
- **Learning Objective:** Separate a small reusable vehicle calculation into an importable module.

## Scenario
A utility module provides a consistent conversion used by several offline vehicle reports.

## Function Details
- **Required Python interface:** Create `vehicle_utilities.py` with `km_to_miles(distance_km: float) -> float` and a caller that imports it.
- **Behavior:** Return distance converted by `0.621371`, rounded to two decimal places. Reject negative distances with `ValueError`.
- **Return shape:** Return a `float` rounded to two decimal places.
- **Input rules and constraints:** `distance_km` is a finite number from 0 through 100000 km. Additional constraints: Keep conversion logic in the module, not duplicated in the caller; Use Python 3.12+; Work with deterministic offline values only.

## Tasks to Implement
1. Implement the specified Python interface: Create `vehicle_utilities.py` with `km_to_miles(distance_km: float) -> float` and a caller that imports it.
2. Apply the stated input validation and constraints: `distance_km` is a finite number from 0 through 100000 km.
3. Implement the required behavior: Return distance converted by `0.621371`, rounded to two decimal places. Reject negative distances with `ValueError`.
4. Return the specified result shape without changing the required ordering or formatting: Return a `float` rounded to two decimal places.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `km_to_miles(0.0)` | `0.0` |
| 2 | `km_to_miles(1.0)` | `0.62` |
| 3 | `km_to_miles(10.0)` | `6.21` |
| 4 | `km_to_miles(160.9344)` | `100.0` |
| 5 | `km_to_miles(100000.0)` | `62137.1` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Functions, return values, type hints, and basic imports.

### Rules and Constraints

- Keep conversion logic in the module, not duplicated in the caller.
- Use Python 3.12+.
- Work with deterministic offline values only.

### Hints

Put the function at module scope and import its public name explicitly.

### Common Mistakes

- Reversing the conversion factor.
- Returning an unrounded value.
- Placing the function only inside a script entry point.

### Extension Challenge

Add `miles_to_km(miles: float) -> float` with the same validation policy.
