# 08 - Sensor Readings - Easy

## Question Details
- Concept: for loops
- Supporting concepts: Lists, aggregation, numeric validation
- Difficulty: Easy
- Domain: Sensor data processing
- Learning Objective: Iterate through sensor readings and calculate a summary.

## Scenario
A simulated temperature sensor produces readings in degrees Celsius during a vehicle test.

## Function Details
- Function signature: `summarize_temperatures(readings: list[float]) -> dict[str, float | int]`
- Behavior / return shape: Count readings, calculate their average, and count readings above 40 degrees Celsius.
- Exact accepted inputs: Readings contain 1 to 10,000 values from -50 through 150 degrees Celsius. Reject invalid input with `ValueError`.
- Output and validation / behavior: Return `count`, `average_c`, and `above_40_count`; average is rounded to two decimals.

## Tasks to Implement
1. Implement `summarize_temperatures` with the exact signature above and validate the inputs against these accepted rules: Readings contain 1 to 10,000 values from -50 through 150 degrees Celsius. Reject invalid input with `ValueError`.
2. Count readings, calculate their average, and count readings above 40 degrees Celsius.
3. Implement this output contract exactly: Return `count`, `average_c`, and `above_40_count`; average is rounded to two decimals.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | summarize_temperatures([-50]) | {"count": 1, "average_c": -50.0, "above_40_count": 0} | Typical valid input. |
| 2 | summarize_temperatures([-50, 150]) | {"count": 2, "average_c": 50.0, "above_40_count": 1} | Valid boundary case. |
| 3 | summarize_temperatures([40, 41, 39]) | {"count": 3, "average_c": 40.0, "above_40_count": 1} | Checks the rule at a threshold. |
| 4 | summarize_temperatures([0, 40, 41, 150]) | {"count": 4, "average_c": 57.75, "above_40_count": 2} | Checks another valid input shape. |
| 5 | summarize_temperatures([-10, 10, 30, 50]) | {"count": 4, "average_c": 20.0, "above_40_count": 1} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of summarize_temperatures that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, functions, loops, arithmetic, and comparisons.

### Rules and Constraints
- Use a for loop.
- Do not use external libraries.
- Do not mutate the list.

### Hints
1. Initialize a total and counter.
2. Increment the high-temperature counter conditionally.
3. Divide only after validating the list is non-empty.

### Common Mistakes
- Counting 40 as above 40.
- Dividing before checking for emptiness.
- Rounding every reading first.

### Extension Challenge
Also return the minimum and maximum readings.
