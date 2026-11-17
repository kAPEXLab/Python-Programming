# 06 - Temperature Warning - Easy

## Question Details
- Concept: if statements
- Supporting concepts: Numeric comparisons, validation, return values
- Difficulty: Easy
- Domain: Battery temperature monitoring
- Learning Objective: Use a simple conditional to classify a simulated battery temperature.

## Scenario
A battery monitoring program classifies a temperature in degrees Celsius. For this exercise, values below 0 are COLD, 0 through 45 are NORMAL, and values above 45 are not handled by this introductory task and must be rejected.

## Function Details
- Function signature: `classify_battery_temperature(temperature_c: float) -> str`
- Behavior / return shape: Return the temperature status for a valid simulated reading.
- Exact accepted inputs: Temperature must be from -40 through 45 degrees Celsius. Reject other values with `ValueError`.
- Output and validation / behavior: Return `COLD` below 0 and `NORMAL` otherwise.

## Tasks to Implement
1. Implement `classify_battery_temperature` with the exact signature above and validate the inputs against these accepted rules: Temperature must be from -40 through 45 degrees Celsius. Reject other values with `ValueError`.
2. Return the temperature status for a valid simulated reading.
3. Implement this output contract exactly: Return `COLD` below 0 and `NORMAL` otherwise.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | classify_battery_temperature(-40) | COLD | Typical valid input. |
| 2 | classify_battery_temperature(-0.1) | COLD | Valid lower or upper boundary. |
| 3 | classify_battery_temperature(0) | NORMAL | Checks the threshold rule. |
| 4 | classify_battery_temperature(45) | NORMAL | Checks a second valid shape or aggregate. |
| 5 | classify_battery_temperature(22.5) | NORMAL | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of classify_battery_temperature that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Functions, numbers, comparisons, and if statements.

### Rules and Constraints
- Use an if statement.
- Treat 0 as NORMAL.
- Do not print from the function.

### Hints
1. Validate the allowed range first.
2. Compare the value with zero.
3. Return one of the exact status strings.

### Common Mistakes
- Treating zero as cold.
- Accepting a value above 45.
- Printing instead of returning.

### Extension Challenge
Add HOT for values above 45 and expand the valid range to 80.
