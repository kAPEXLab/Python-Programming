# 16 - Valid Sensor Values - Easy

## Question Details
- Concept: List comprehensions
- Supporting concepts: Filtering, validation, rounding, functions
- Difficulty: Easy
- Domain: Simulated sensor cleanup
- Learning Objective: Use a list comprehension to retain sensor readings inside an inclusive range.

## Scenario
An offline sensor feed includes readings that must be screened before analysis.

## Function Details
- Function signature: `valid_sensor_values(values: list[float], minimum: float, maximum: float) -> list[float]`
- Behavior / return shape: Return valid temperature readings in their original order.
- Exact accepted inputs: Values are finite numbers; bounds are finite with `minimum <= maximum`. Keep values from -50.0 through 150.0 that are between the provided bounds inclusively.
- Output and validation / behavior: Return a new list containing only qualifying values, without rounding or reordering.

## Tasks to Implement
1. Implement `valid_sensor_values` with the exact signature above and validate the inputs against these accepted rules: Values are finite numbers; bounds are finite with `minimum <= maximum`. Keep values from -50.0 through 150.0 that are between the provided bounds inclusively.
2. Return valid temperature readings in their original order.
3. Implement this output contract exactly: Return a new list containing only qualifying values, without rounding or reordering.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | valid_sensor_values([0, 1, 2], 0, 1) | [0, 1] | Typical valid input. |
| 2 | valid_sensor_values([1, 2, 3], 2, 2) | [2] | Valid boundary case. |
| 3 | valid_sensor_values([-50, 0, 150], -50, 150) | [-50, 0, 150] | Checks the threshold rule. |
| 4 | valid_sensor_values([10, 20, 30], 15, 25) | [20] | Checks an alternate valid shape. |
| 5 | valid_sensor_values([], 0, 1) | [] | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of valid_sensor_values that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, comparisons, numbers, functions, and validation.

### Rules and Constraints
- Use a list comprehension for filtering.
- Reject non-finite values and invalid bounds with ValueError.
- Do not mutate input.

### Hints
1. Validate the full input before the comprehension.
2. Use minimum <= value <= maximum.
3. The result list should be independent of the input list.

### Common Mistakes
- Excluding exact boundary values.
- Sorting filtered readings.
- Returning the original list when all values match.

### Extension Challenge
Return the valid readings rounded to one decimal place using a second comprehension.
