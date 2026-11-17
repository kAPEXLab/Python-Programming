# 13 - GPS Coordinate - Medium

## Question Details
- Concept: Tuple packing and unpacking
- Supporting concepts: Nested tuples, validation, rounding, functions
- Difficulty: Medium
- Domain: Simulated GPS coordinates
- Learning Objective: Unpack nested coordinate tuples and return a normalized location record.

## Scenario
An offline navigation exercise represents a position as (latitude, longitude, altitude_m), with no live location service.

## Function Details
- Function signature: `normalize_gps_coordinate(coordinate: tuple[float, float, float]) -> tuple[float, float, float]`
- Behavior / return shape: Validate and format a coordinate for a route log.
- Exact accepted inputs: Latitude is -90.0 to 90.0 degrees, longitude is -180.0 to 180.0 degrees, and altitude is -500.0 to 9000.0 meters. All values are finite numbers.
- Output and validation / behavior: Return a packed tuple `(latitude, longitude, altitude_m)` rounded to 4, 4, and 1 decimal places respectively.

## Tasks to Implement
1. Implement `normalize_gps_coordinate` with the exact signature above and validate the inputs against these accepted rules: Latitude is -90.0 to 90.0 degrees, longitude is -180.0 to 180.0 degrees, and altitude is -500.0 to 9000.0 meters. All values are finite numbers.
2. Validate and format a coordinate for a route log.
3. Implement this output contract exactly: Return a packed tuple `(latitude, longitude, altitude_m)` rounded to 4, 4, and 1 decimal places respectively.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | normalize_gps_coordinate((0, 0, 0)) | (0, 0, 0) | Typical valid input. |
| 2 | normalize_gps_coordinate((-90, -180, -500)) | (-90, -180, -500) | Valid boundary case. |
| 3 | normalize_gps_coordinate((90, 180, 9000)) | (90, 180, 9000) | Checks the threshold rule. |
| 4 | normalize_gps_coordinate((37.7749, -122.4194, 15.25)) | (37.7749, -122.4194, 15.3) | Checks an alternate valid shape. |
| 5 | normalize_gps_coordinate((1.23456, 2.34567, 123.45)) | (1.2346, 2.3457, 123.5) | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of normalize_gps_coordinate that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Tuples, floating-point arithmetic, dictionaries, validation, and functions.

### Rules and Constraints
- Unpack all three values before validation.
- Raise ValueError for wrong shape or range violations.
- Use standard Python round; do not convert units.

### Hints
1. Use tuple unpacking before computing the output.
2. Validate with numeric range checks.
3. Pack the three rounded values in the original order.

### Common Mistakes
- Swapping latitude and longitude.
- Rounding altitude to four places.
- Treating altitude as required to be nonnegative.

### Extension Challenge
Accept a second coordinate and return the component-wise midpoint rounded with the same rules.
