# 02 - Fuel Reading - Medium

## Question Details
- Concept: Variables and naming conventions
- Supporting concepts: Numeric types, unit conversion, validation, arithmetic
- Difficulty: Medium
- Domain: Fuel consumption monitoring
- Learning Objective: Calculate fuel consumed, liters per 100 km, and remaining fuel from validated trip readings.

## Scenario
Calculate fuel economy and remaining fuel after a trip.

## Function Details
- Function signature: `calculate_fuel_reading(start_liters: float, fuel_added_liters: float, end_liters: float, distance_km: float) -> dict[str, float]`
- Behavior / return shape: Calculate fuel economy and remaining fuel after a trip.
- Exact accepted inputs: All fuel values are numbers from 0 through 200 liters; `distance_km` is a number from 0.1 through 5,000 km; Fuel use is `start_liters + fuel_added_liters - end_liters`; Reject negative fuel use or an end level greater than available fuel with `ValueError`.
- Output and validation / behavior: Return `fuel_used_liters`, `fuel_economy_l_per_100km`, and `remaining_liters` as numeric values rounded to two decimals; fuel economy is in liters per 100 km.

## Tasks to Implement
1. Implement `calculate_fuel_reading` with the exact signature above and validate the inputs against these accepted rules: All fuel values are numbers from 0 through 200 liters; `distance_km` is a number from 0.1 through 5,000 km; Fuel use is `start_liters + fuel_added_liters - end_liters`; Reject negative fuel use or an end level greater than available fuel with `ValueError`.
2. Compute fuel used as `start_liters + fuel_added_liters - end_liters`, calculate L/100 km from the unrounded fuel use, and include the remaining fuel.
3. Implement this output contract exactly: Return `fuel_used_liters`, `fuel_economy_l_per_100km`, and `remaining_liters` as numeric values rounded to two decimals; fuel economy is in liters per 100 km.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | calculate_fuel_reading(40, 10, 30, 100) | {"fuel_used_liters": 20.0, "fuel_economy_l_per_100km": 20.0, "remaining_liters": 30.0} | Typical valid input. |
| 2 | calculate_fuel_reading(0, 200, 100, 5000) | {"fuel_used_liters": 100.0, "fuel_economy_l_per_100km": 2.0, "remaining_liters": 100.0} | Valid boundary or threshold case. |
| 3 | calculate_fuel_reading(200, 0, 0, 50) | {"fuel_used_liters": 200.0, "fuel_economy_l_per_100km": 400.0, "remaining_liters": 0.0} | Checks an alternate accepted value or input shape. |
| 4 | calculate_fuel_reading(100, 50, 100, 250) | {"fuel_used_liters": 50.0, "fuel_economy_l_per_100km": 20.0, "remaining_liters": 100.0} | Checks a second valid boundary or aggregation case. |
| 5 | calculate_fuel_reading(10, 0, 9.5, 0.1) | {"fuel_used_liters": 0.5, "fuel_economy_l_per_100km": 500.0, "remaining_liters": 9.5} | Checks another valid input without changing the contract. |

## Expected Deliverables
- Complete implementation of calculate_fuel_reading that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
- Do not round intermediate calculations; round each value only when constructing the return dictionary.
- Do not modify the input values.
