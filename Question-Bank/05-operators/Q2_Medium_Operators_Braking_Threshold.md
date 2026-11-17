# 05 - Braking Threshold - Medium

## Question Details
- Concept: Comparison and logical operators
- Supporting concepts: Boolean expressions, validation, unit thresholds
- Difficulty: Medium
- Domain: Offline braking-event analysis
- Learning Objective: Combine comparison and logical operators to classify simulated braking events.

## Scenario
A simulated vehicle log records speed before braking, speed after braking, and elapsed braking time. A hard-braking event is defined as a speed reduction of at least 30 km/h in no more than 3 seconds.

## Function Details
- Function signature: `classify_braking_event(speed_before_kmh: float, speed_after_kmh: float, duration_seconds: float) -> str`
- Behavior / return shape: Classify one event as HARD_BRAKING or NORMAL_BRAKING.
- Exact accepted inputs: Speeds are 0 through 300 km/h; duration is 0.01 through 60 seconds. After-speed cannot exceed before-speed. Reject invalid data with `ValueError`.
- Output and validation / behavior: Return `HARD_BRAKING` when the speed reduction is at least 30 km/h and braking duration is at most 3 seconds; otherwise return `NORMAL_BRAKING`. Both thresholds are inclusive.

## Tasks to Implement
1. Implement `classify_braking_event` with the exact signature above and validate the inputs against these accepted rules: Speeds are 0 through 300 km/h; duration is 0.01 through 60 seconds. After-speed cannot exceed before-speed. Reject invalid data with `ValueError`.
2. Classify one event as HARD_BRAKING or NORMAL_BRAKING.
3. Implement this output contract exactly: Return `HARD_BRAKING` when the speed reduction is at least 30 km/h and braking duration is at most 3 seconds; otherwise return `NORMAL_BRAKING`. Both thresholds are inclusive.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | classify_braking_event(60, 30, 3) | HARD_BRAKING | Typical valid input. |
| 2 | classify_braking_event(100, 70, 3) | HARD_BRAKING | Valid lower or upper boundary. |
| 3 | classify_braking_event(100, 69.9, 3) | HARD_BRAKING | Checks the threshold rule. |
| 4 | classify_braking_event(80, 50, 3.01) | NORMAL_BRAKING | Checks a second valid shape or aggregate. |
| 5 | classify_braking_event(0, 0, 0.01) | NORMAL_BRAKING | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of classify_braking_event that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Functions, booleans, comparisons, arithmetic, and conditionals.

### Rules and Constraints
- Use a compound boolean expression.
- A reduction exactly 30 km/h and duration exactly 3 seconds qualifies.
- Do not round before comparing.

### Hints
1. Compute speed reduction once.
2. Use and to combine both qualifying conditions.
3. Check input consistency before classification.

### Common Mistakes
- Using or instead of and.
- Making thresholds exclusive.
- Ignoring impossible speed order.

### Extension Challenge
Return a dictionary containing reduction, duration, and classification.
