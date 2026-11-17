# 12 - Speed History - Easy

## Question Details
- Concept: Lists and basic slicing
- Supporting concepts: Indexing, validation, arithmetic, functions
- Difficulty: Easy
- Domain: Simulated vehicle speed history
- Learning Objective: Use list indexing and slices to inspect a recent portion of an ordered speed history.

## Scenario
An offline driving simulation stores speed readings in kilometers per hour from oldest to newest.

## Function Details
- Function signature: `summarize_speed_history(readings: list[int]) -> dict[str, object]`
- Behavior / return shape: Return the first reading, last reading, and the most recent three readings.
- Exact accepted inputs: `readings` must contain 3 through 100 integer speeds from 0 through 240 km/h. Boolean values are invalid.
- Output and validation / behavior: Return `first`, `last`, and `recent_three`, preserving integer values and input order.

## Tasks to Implement
1. Implement `summarize_speed_history` with the exact signature above and validate the inputs against these accepted rules: `readings` must contain 3 through 100 integer speeds from 0 through 240 km/h. Boolean values are invalid.
2. Return the first reading, last reading, and the most recent three readings.
3. Implement this output contract exactly: Return `first`, `last`, and `recent_three`, preserving integer values and input order.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | summarize_speed_history([0, 1, 2]) | {"first": 0, "last": 2, "recent_three": [0, 1, 2]} | Typical valid input. |
| 2 | summarize_speed_history([10, 20, 30, 40]) | {"first": 10, "last": 40, "recent_three": [20, 30, 40]} | Valid boundary case. |
| 3 | summarize_speed_history([240, 0, 120]) | {"first": 240, "last": 120, "recent_three": [240, 0, 120]} | Checks the threshold rule. |
| 4 | summarize_speed_history([1, 2, 3, 4, 5, 6]) | {"first": 1, "last": 6, "recent_three": [4, 5, 6]} | Checks an alternate valid shape. |
| 5 | summarize_speed_history([55, 60, 65, 70, 75]) | {"first": 55, "last": 75, "recent_three": [65, 70, 75]} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of summarize_speed_history that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Variables, numbers, lists, functions, and conditionals.

### Rules and Constraints
- Use indexing for the first and last readings.
- Use a slice for recent_three.
- Raise ValueError for invalid input.
- Do not mutate the list.

### Hints
1. Validate every item before indexing.
2. The last item has index -1.
3. The slice [-3:] selects the recent readings.

### Common Mistakes
- Sorting the readings before returning them.
- Returning a tuple instead of a list for the slice.
- Accepting out-of-range speeds.

### Extension Challenge
Also return the average of the recent three readings rounded to one decimal place.
