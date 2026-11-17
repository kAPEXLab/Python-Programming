# 13 - Wheel Alignment - Easy

## Question Details
- Concept: Tuple packing and unpacking
- Supporting concepts: Numeric validation, indexing, functions
- Difficulty: Easy
- Domain: Offline wheel alignment readings
- Learning Objective: Pack alignment measurements into tuples and unpack them into named values.

## Scenario
A workshop simulation records camber, caster, and toe angles in degrees for one wheel.

## Function Details
- Function signature: `check_wheel_alignment(measurements: tuple[float, float, float]) -> str`
- Behavior / return shape: Classify whether a wheel is aligned based on fixed tolerances.
- Exact accepted inputs: The tuple is `(camber, caster, toe)` with finite values from -10.0 through 10.0 degrees.
- Output and validation / behavior: Return `"ALIGNED"` when absolute camber is at most 1.0, absolute caster is at most 2.0, and absolute toe is at most 0.5; otherwise return `"ADJUST"`.

## Tasks to Implement
1. Implement `check_wheel_alignment` with the exact signature above and validate the inputs against these accepted rules: The tuple is `(camber, caster, toe)` with finite values from -10.0 through 10.0 degrees.
2. Classify whether a wheel is aligned based on fixed tolerances.
3. Implement this output contract exactly: Return `"ALIGNED"` when absolute camber is at most 1.0, absolute caster is at most 2.0, and absolute toe is at most 0.5; otherwise return `"ADJUST"`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | check_wheel_alignment((0, 0, 0)) | ALIGNED | Typical valid input. |
| 2 | check_wheel_alignment((1, 2, 0.5)) | ALIGNED | Valid boundary case. |
| 3 | check_wheel_alignment((1.01, 0, 0)) | ADJUST | Checks the threshold rule. |
| 4 | check_wheel_alignment((0, 2.01, 0)) | ADJUST | Checks an alternate valid shape. |
| 5 | check_wheel_alignment((-1, -2, -0.5)) | ALIGNED | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of check_wheel_alignment that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Variables, tuples, arithmetic, functions, and conditionals.

### Rules and Constraints
- Unpack the tuple in one assignment.
- Require exactly three numeric values and reject booleans with ValueError.
- Do not change the input tuple.

### Hints
1. Validate length and numeric types first.
2. Unpack as camber, caster, toe.
3. Compare absolute values with inclusive limits.

### Common Mistakes
- Comparing only positive deviations.
- Requiring values to be strictly inside limits.
- Accepting a list when a tuple is required.

### Extension Challenge
Return the first measurement name that exceeds its tolerance.
