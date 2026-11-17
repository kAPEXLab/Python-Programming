# 05 - Fuel Economy - Easy

## Question Details
- Concept: Operators and expressions
- Supporting concepts: Numeric types, conversion, rounding
- Difficulty: Easy
- Domain: Fuel-efficiency analysis
- Learning Objective: Use arithmetic operators to calculate fuel economy accurately.

## Scenario
Fuel economy describes fuel used for a distance. This exercise reports liters per 100 km from a trip's fuel and distance.

## Function Details
- Function signature: `fuel_economy(fuel_liters: float, distance_km: float) -> float`
- Behavior / return shape: Calculate fuel economy using the formula fuel_liters / distance_km * 100.
- Exact accepted inputs: Fuel is 0 through 500 liters; distance is 0.1 through 5,000 km. Reject invalid values with `ValueError`.
- Output and validation / behavior: Return a float rounded to two decimal places in liters per 100 km, calculated as fuel liters divided by distance km times 100; zero fuel returns `0.0`.

## Tasks to Implement
1. Implement `fuel_economy` with the exact signature above and validate the inputs against these accepted rules: Fuel is 0 through 500 liters; distance is 0.1 through 5,000 km. Reject invalid values with `ValueError`.
2. Calculate fuel economy using the formula fuel_liters / distance_km * 100.
3. Implement this output contract exactly: Return a float rounded to two decimal places in liters per 100 km, calculated as fuel liters divided by distance km times 100; zero fuel returns `0.0`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | fuel_economy(0.1, 0.1) | 100.0 | Exercises the minimum permitted positive fuel and distance values. |
| 2 | fuel_economy(0, 0.1) | 0 | Valid lower or upper boundary. |
| 3 | fuel_economy(5, 100) | 5 | Checks the threshold rule. |
| 4 | fuel_economy(500, 5000) | 10 | Checks a second valid shape or aggregate. |
| 5 | fuel_economy(12.5, 250) | 5 | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of fuel_economy that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Variables, functions, numeric values, and formatted output.

### Rules and Constraints
- Follow the formula exactly.
- Do not divide by zero.
- Do not print from the function.

### Hints
1. Validate distance before division.
2. Apply multiplication by 100 after division.
3. Round only the result.

### Common Mistakes
- Reversing fuel and distance.
- Using integer division.
- Treating zero fuel as invalid.

### Extension Challenge
Return both liters per 100 km and kilometers per liter.
