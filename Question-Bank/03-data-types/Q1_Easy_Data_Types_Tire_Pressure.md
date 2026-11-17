# 03 - Tire Pressure - Easy

## Question Details
- Concept: Numeric data types, booleans, and type conversion
- Supporting concepts: Functions, validation, formatted output
- Difficulty: Easy
- Domain: Tire-pressure monitoring
- Learning Objective: Convert a numeric pressure reading and classify it using boolean comparisons.

## Scenario
A tire-pressure monitoring system reports pressure in kilopascals (kPa). For this exercise, a tire is considered correctly inflated from 220 through 250 kPa inclusive.

## Function Details
- Function signature: `check_tire_pressure(pressure_kpa: float) -> dict[str, object]`
- Behavior / return shape: Return a record containing the pressure converted to bar and whether it is in the recommended range.
- Exact accepted inputs: `pressure_kpa` is a number from 0 through 500 kPa. Reject other values with `ValueError`.
- Output and validation / behavior: Return `pressure_kpa`, `pressure_bar`, and `is_recommended` in a dictionary. Convert using `1 bar = 100 kPa`, round both pressure values to two decimals, and set `is_recommended` to true only from 220 through 250 kPa inclusive.

## Tasks to Implement
1. Implement `check_tire_pressure` with the exact signature above and validate the inputs against these accepted rules: `pressure_kpa` is a number from 0 through 500 kPa. Reject other values with `ValueError`.
2. Return a record containing the pressure converted to bar and whether it is in the recommended range.
3. Implement this output contract exactly: Return `pressure_kpa`, `pressure_bar`, and `is_recommended` in a dictionary. Convert using `1 bar = 100 kPa`, round both pressure values to two decimals, and set `is_recommended` to true only from 220 through 250 kPa inclusive.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | check_tire_pressure(0) | {"pressure_kpa": 0, "pressure_bar": 0.0, "is_recommended": False} | Typical valid input. |
| 2 | check_tire_pressure(220) | {"pressure_kpa": 220, "pressure_bar": 2.2, "is_recommended": True} | Valid boundary or threshold case. |
| 3 | check_tire_pressure(250) | {"pressure_kpa": 250, "pressure_bar": 2.5, "is_recommended": True} | Checks an alternate accepted value or input shape. |
| 4 | check_tire_pressure(500) | {"pressure_kpa": 500, "pressure_bar": 5.0, "is_recommended": False} | Checks a second valid boundary or aggregation case. |
| 5 | check_tire_pressure(232.5) | {"pressure_kpa": 232.5, "pressure_bar": 2.33, "is_recommended": True} | Checks another valid input without changing the contract. |

## Expected Deliverables
- Complete implementation of check_tire_pressure that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Variables, numbers, booleans, comparisons, and functions.

### Rules and Constraints
- Use numeric types deliberately; do not convert through formatted text.
- The recommended interval is inclusive.
- Do not print from the function.

### Hints
1. Divide kPa by 100 to obtain bar.
2. Combine two inclusive comparisons.
3. Return the boolean directly.

### Common Mistakes
- Using strict inequalities at the boundaries.
- Multiplying instead of dividing by 100.
- Returning the text "True" instead of a boolean.

### Extension Challenge
Accept either kPa or bar through a validated unit argument.
