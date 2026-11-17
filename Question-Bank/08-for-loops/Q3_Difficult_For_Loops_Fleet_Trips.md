# 08 - Fleet Trips - Difficult

## Question Details
- Concept: for loops and multi-record aggregation
- Supporting concepts: Dictionaries, validation, grouping, rounding
- Difficulty: Difficult
- Domain: Fleet trip analysis
- Learning Objective: Aggregate large collections with a loop while grouping results by vehicle.

## Scenario
A fleet manager receives simulated trip records. Each record includes a vehicle ID, distance in km, and energy used in kWh.

## Function Details
- Function signature: `summarize_fleet_trips(trips: list[dict[str, object]]) -> dict[str, object]`
- Behavior / return shape: Calculate per-vehicle distance, energy, and efficiency, then identify the most efficient vehicle.
- Exact accepted inputs: 0 to 100,000 records; Vehicle ID is a non-empty string; Distance is 0 through 2,000 km; energy is 0 through 500 kWh; Each vehicle must have positive total distance; Reject malformed records with `ValueError`.
- Output and validation / behavior: For each vehicle return `distance_km`, `energy_kwh`, and `wh_per_km`, where `wh_per_km = energy_kwh * 1000 / distance_km`, rounded to two decimals. Empty input returns an empty vehicle dictionary and `None` best vehicle.

## Tasks to Implement
1. Implement `summarize_fleet_trips` with the exact signature above and validate the inputs against these accepted rules: 0 to 100,000 records; Vehicle ID is a non-empty string; Distance is 0 through 2,000 km; energy is 0 through 500 kWh; Each vehicle must have positive total distance; Reject malformed records with `ValueError`.
2. Calculate per-vehicle distance, energy, and efficiency, then identify the most efficient vehicle.
3. Return exactly the specified result: For each vehicle return `distance_km`, `energy_kwh`, and `wh_per_km`, where `wh_per_km = energy_kwh * 1000 / distance_km`, rounded to two decimals. Empty input returns an empty vehicle dictionary and `None` best vehicle.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | summarize_fleet_trips([{"vehicle_id": "V1", "distance_km": 100.0, "energy_kwh": 20.0}]) | {"vehicles": {"V1": {"distance_km": 100.0, "energy_kwh": 20.0, "wh_per_km": 200.0}}, "best_vehicle": "V1"} | Typical valid input. |
| 2 | summarize_fleet_trips([{"vehicle_id": "V1", "distance_km": 50.0, "energy_kwh": 10.0}, {"vehicle_id": "V1", "distance_km": 50.0, "energy_kwh": 15.0}]) | {"vehicles": {"V1": {"distance_km": 100.0, "energy_kwh": 25.0, "wh_per_km": 250.0}}, "best_vehicle": "V1"} | Valid boundary case. |
| 3 | summarize_fleet_trips([{"vehicle_id": "B", "distance_km": 100.0, "energy_kwh": 10.0}, {"vehicle_id": "A", "distance_km": 100.0, "energy_kwh": 20.0}]) | {"vehicles": {"B": {"distance_km": 100.0, "energy_kwh": 10.0, "wh_per_km": 100.0}, "A": {"distance_km": 100.0, "energy_kwh": 20.0, "wh_per_km": 200.0}}, "best_vehicle": "B"} | Checks the rule at a threshold. |
| 4 | summarize_fleet_trips([{"vehicle_id": "EV", "distance_km": 1.0, "energy_kwh": 0.0}]) | {"vehicles": {"EV": {"distance_km": 1.0, "energy_kwh": 0.0, "wh_per_km": 0.0}}, "best_vehicle": "EV"} | Checks another valid input shape. |
| 5 | summarize_fleet_trips([]) | {"vehicles": {}, "best_vehicle": None} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of summarize_fleet_trips that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Loops, dictionaries, functions, validation, arithmetic, and formatted data.

### Rules and Constraints
- Use a for loop and one-pass aggregation.
- Do not sort all records to find the best vehicle.
- Preserve first-seen vehicle order in the returned dictionary.
- Do not mutate inputs.

### Hints
1. Use an insertion-ordered dictionary for running totals.
2. Validate records while processing them.
3. Compare each completed vehicle's efficiency once.

### Common Mistakes
- Calculating efficiency per trip and averaging it.
- Dividing by a zero total distance.
- Sorting when a running best is sufficient.

### Extension Challenge
Return the least efficient vehicle and its efficiency as well.
