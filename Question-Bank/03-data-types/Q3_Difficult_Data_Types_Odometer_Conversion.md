# 03 - Odometer Conversion - Difficult

## Question Details
- Concept: Numeric types and safe type conversion
- Supporting concepts: Dictionaries, validation, unit conversion, rounding
- Difficulty: Difficult
- Domain: Odometer and distance reporting
- Learning Objective: Build a robust conversion function that handles multiple units, numeric validation, and precision requirements.

## Scenario
An odometer stores distance in kilometers, while some reports require miles. The conversion is 1 km = 0.621371 miles.

## Function Details
- Function signature: `convert_odometer(distance: float | int, unit: str) -> dict[str, object]`
- Behavior / return shape: Convert a distance from kilometers or miles into both units and classify whether it is a plausible odometer reading.
- Exact accepted inputs: `distance` is from 0 through 2,000,000 in the supplied unit; `unit` is `km` or `mi`, ignoring surrounding whitespace and case; Reject booleans, nonnumeric values, invalid units, and out-of-range distances with `ValueError`.
- Output and validation / behavior: Return `kilometers`, `miles`, and `is_plausible` in a dictionary; convert using `1 km = 0.621371 miles`, round both distances to two decimals, and mark the reading plausible when kilometers are at most 2,000,000.

## Tasks to Implement
1. Implement `convert_odometer` with the exact signature above and validate the inputs against these accepted rules: `distance` is from 0 through 2,000,000 in the supplied unit; `unit` is `km` or `mi`, ignoring surrounding whitespace and case; Reject booleans, nonnumeric values, invalid units, and out-of-range distances with `ValueError`.
2. Convert a distance from kilometers or miles into both units and classify whether it is a plausible odometer reading.
3. Implement this output contract exactly: Return `kilometers`, `miles`, and `is_plausible` in a dictionary; convert using `1 km = 0.621371 miles`, round both distances to two decimals, and mark the reading plausible when kilometers are at most 2,000,000.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | convert_odometer(0, "km") | {"kilometers": 0.0, "miles": 0.0, "is_plausible": True} | Typical valid input. |
| 2 | convert_odometer(2000000, "km") | {"kilometers": 2000000.0, "miles": 1242742.0, "is_plausible": True} | Valid lower or upper boundary. |
| 3 | convert_odometer(0, "mi") | {"kilometers": 0.0, "miles": 0.0, "is_plausible": True} | Checks the threshold rule. |
| 4 | convert_odometer(100, "mi") | {"kilometers": 160.93, "miles": 100.0, "is_plausible": True} | Checks a second valid shape or aggregate. |
| 5 | convert_odometer(1609.34, " KM ") | {"kilometers": 1609.34, "miles": 1000.0, "is_plausible": True} | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of convert_odometer that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Functions, dictionaries, numeric types, conditionals, exceptions, and rounding.

### Rules and Constraints
- Use the stated conversion constant exactly.
- Treat True and False as invalid numeric measurements.
- Do not round before the final output.
- Do not modify the input values.

### Hints
1. Normalize the unit before branching.
2. Convert the supplied value into a canonical kilometer value first.
3. Apply rounding only in the returned dictionary.

### Common Mistakes
- Applying the conversion factor in the wrong direction.
- Treating booleans as valid distances.
- Rounding the canonical value too early.

### Extension Challenge
Add nautical miles as an output-only field using 1 km = 0.539957 nautical miles.
