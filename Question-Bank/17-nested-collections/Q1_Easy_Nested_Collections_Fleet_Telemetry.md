# 17 - Fleet Telemetry - Easy

## Question Details
- Concept: Nested lists and dictionaries
- Supporting concepts: Traversal, validation, aggregation, functions
- Difficulty: Easy
- Domain: Offline fleet telemetry
- Learning Objective: Traverse nested vehicle records to calculate fleet speed statistics.

## Scenario
A simulated fleet report contains vehicle IDs and ordered speed readings.

## Function Details
- Function signature: `fleet_speed_average(telemetry: list[dict[str, object]]) -> dict[str, object]`
- Behavior / return shape: Return the total reading count and fleet-wide average speed.
- Exact accepted inputs: Each record has a non-empty string `vehicle_id` and a `speeds` list of 0 through 100 integer values from 0 through 240 km/h. IDs are unique.
- Output and validation / behavior: Return `vehicle_count`, `reading_count`, and `average_speed_kmh`, rounded to two decimals; an empty reading set has average `None`.

## Tasks to Implement
1. Implement `fleet_speed_average` with the exact signature above and validate the inputs against these accepted rules: Each record has a non-empty string `vehicle_id` and a `speeds` list of 0 through 100 integer values from 0 through 240 km/h. IDs are unique.
2. Return the total reading count and fleet-wide average speed.
3. Implement this output contract exactly: Return `vehicle_count`, `reading_count`, and `average_speed_kmh`, rounded to two decimals; an empty reading set has average `None`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | fleet_speed_average([{"vehicle_id": "A", "speeds": [0, 100]}]) | {"vehicle_count": 1, "reading_count": 2, "average_speed_kmh": 50.0} | Typical valid input. |
| 2 | fleet_speed_average([{"vehicle_id": "A", "speeds": []}]) | {"vehicle_count": 1, "reading_count": 0, "average_speed_kmh": None} | Valid boundary case. |
| 3 | fleet_speed_average([{"vehicle_id": "A", "speeds": [60, 80]}, {"vehicle_id": "B", "speeds": [100]}]) | {"vehicle_count": 2, "reading_count": 3, "average_speed_kmh": 80.0} | Checks an empty or alternate shape. |
| 4 | fleet_speed_average([]) | {"vehicle_count": 0, "reading_count": 0, "average_speed_kmh": None} | Checks an aggregation boundary. |
| 5 | fleet_speed_average([{"vehicle_id": "EV", "speeds": [240]}]) | {"vehicle_count": 1, "reading_count": 1, "average_speed_kmh": 240.0} | Checks multiple records. |

## Expected Deliverables
- Complete implementation of fleet_speed_average that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, dictionaries, loops, numbers, and validation.

### Rules and Constraints
- Traverse every nested speed list.
- Reject malformed records with ValueError.
- Do not mutate input.

### Hints
1. Validate the outer record shape first.
2. Maintain a total and count while traversing inner values.
3. Handle count zero before division.

### Common Mistakes
- Averaging vehicle averages without weighting by readings.
- Ignoring vehicles with empty lists.
- Mutating the nested records.

### Extension Challenge
Return each vehicle's average alongside the fleet average.
