---
layout: default
---

# 02_Variables_FuelReading

**Difficulty:** Medium  
**Primary Python Concept:** Variables and naming conventions  
**Supporting Concepts:** Numeric types, unit conversion, validation, arithmetic  
**Automotive Domain:** Fuel consumption monitoring  
**Estimated Completion Time:** 35 minutes

## Problem Statement
**Your goal:** Calculate fuel economy and remaining fuel after a trip.

## Task to Implement
Implement `calculate_fuel_reading(start_liters: float, fuel_added_liters: float, end_liters: float, distance_km: float) -> dict[str, float]`. Return keys `fuel_used_liters`, `fuel_economy_l_per_100km`, and `remaining_liters`, each rounded to two decimals.

## Input Specification
- All fuel values are numbers from 0 through 200 liters.
- `distance_km` is a number from 0.1 through 5,000 km.
- Fuel use is `start_liters + fuel_added_liters - end_liters`.
- Reject negative fuel use or an end level greater than available fuel with `ValueError`.

## Output Specification
Return a dictionary with the three specified keys and numeric values rounded to two decimals. Fuel economy is in liters per 100 km.

## Rules and Constraints
- Use descriptive names that include units where useful.
- Do **not** round intermediate values.
- Do **not** mutate inputs.
- Raise `ValueError` for invalid ranges or physically inconsistent readings.

---

## Hint Rubric
- Validate that all inputs are within the allowed ranges.
- Ensure the *available* fuel (`start + added`) is not less than `end_liters`.
- Compute ``fuel_used = start + added - end`` **before** any rounding.
- Fuel economy = ``fuel_used / distance_km * 100`` (L per 100 km).
- Round each result **only when constructing the return dictionary**.
- Return a dictionary with the exact key names required.
