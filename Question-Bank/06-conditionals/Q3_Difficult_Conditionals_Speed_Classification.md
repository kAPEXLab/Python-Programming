# 06 - Speed Classification - Difficult

## Question Details
- Concept: Nested and chained conditional statements
- Supporting concepts: Validation, multiple thresholds, tuple results
- Difficulty: Difficult
- Domain: Offline vehicle-speed analysis
- Learning Objective: Design a multi-level conditional classifier with clear threshold precedence and validation.

## Scenario
A simulated road-speed analyzer classifies speed and road type. It uses different limits: urban 50 km/h, rural 80 km/h, and highway 120 km/h.

## Function Details
- Function signature: `classify_speed(speed_kmh: float, road_type: str) -> tuple[str, str]`
- Behavior / return shape: Return whether a vehicle is within the selected limit and assign a severity label.
- Exact accepted inputs: Speed is 0 through 300 km/h. Road type must be one of the three labels, ignoring surrounding whitespace and case. Reject invalid input with `ValueError`.
- Output and validation / behavior: Return `("WITHIN_LIMIT", "NONE")` within the selected road limit; otherwise return `("OVER_LIMIT", severity)`. Excess from 1–10 km/h is `LOW`, 11–30 is `MEDIUM`, and above 30 is `HIGH` (including exactly 10 as LOW and exactly 30 as MEDIUM).

## Tasks to Implement
1. Implement `classify_speed` with the exact signature above and validate the inputs against these accepted rules: Speed is 0 through 300 km/h. Road type must be one of the three labels, ignoring surrounding whitespace and case. Reject invalid input with `ValueError`.
2. Return whether a vehicle is within the selected limit and assign a severity label.
3. Implement this output contract exactly: Return `("WITHIN_LIMIT", "NONE")` within the selected road limit; otherwise return `("OVER_LIMIT", severity)`. Excess from 1–10 km/h is `LOW`, 11–30 is `MEDIUM`, and above 30 is `HIGH`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | classify_speed(50, "urban") | ("WITHIN_LIMIT", "NONE") | Typical valid input. |
| 2 | classify_speed(60, "urban") | ("OVER_LIMIT", "LOW") | Valid lower or upper boundary. |
| 3 | classify_speed(80, "rural") | ("WITHIN_LIMIT", "NONE") | Checks the threshold rule. |
| 4 | classify_speed(110, "rural") | ("OVER_LIMIT", "MEDIUM") | Checks a second valid shape or aggregate. |
| 5 | classify_speed(121, "highway") | ("OVER_LIMIT", "LOW") | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of classify_speed that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Functions, conditionals, comparisons, tuples, and exceptions.

### Rules and Constraints
- Use a clear conditional structure.
- Compare against the selected road limit.
- Do not silently clamp speed.

### Hints
1. Normalize the road type before selecting a limit.
2. Return immediately for within-limit readings.
3. Calculate excess once and classify it in ascending order.

### Common Mistakes
- Applying one limit to every road type.
- Treating the limit as exclusive.
- Using the wrong severity interval.

### Extension Challenge
Accept a custom limit dictionary as an optional parameter.
