# 27 - Sorting Searching Aggregation Filtering Mapping Reduction Fleet Efficiency - Easy

## Question Details
- **Concept:** Sorting, searching, aggregation, filtering, mapping, and reduction
- **Supporting Python concepts:** Higher-order functions, records, rounding
- **Difficulty:** Easy
- **Domain:** Offline fleet efficiency ranking
- **Learning Objective:** Transform and reduce trip records into a stable efficiency ranking.
- **Estimated completion time:** 60 minutes

## Scenario
A fleet analyst compares vehicles by kilometers per kWh from completed electric trips.

## Function Details
Implement `rank_fleet_efficiency(trips: list[dict[str, object]]) -> list[tuple[str, float]]`.

**Required API / operation:** Filter valid trips, aggregate each vehicle, and rank by descending efficiency.

**Input rules and constraints:** Each record has `vehicle_id` (non-empty string), `distance_km` (>0), and `energy_kwh` (>0). Ignore records with `distance_km < 1.0`; reject malformed records. Values are finite.

**Behavior and return shape:** Return one tuple per vehicle `(vehicle_id, km_per_kwh)`, using total distance divided by total energy, rounded to two decimals. Sort by efficiency descending, then vehicle ID ascending.

**Implementation rules:** Aggregate before dividing. Do not mutate input records. Empty input or all filtered records returns `[]`.

## Tasks to Implement
1. Transform and reduce trip records into a stable efficiency ranking.
2. Filter valid trips, aggregate each vehicle, and rank by descending efficiency.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `trips=[{"vehicle_id":"A","distance_km":100,"energy_kwh":20}]` | `[('A', 5.0)]` |
| 2 | `trips=[{"vehicle_id":"B","distance_km":0.5,"energy_kwh":1}]` | `[]` |
| 3 | `trips=[{"vehicle_id":"A","distance_km":10,"energy_kwh":2},{"vehicle_id":"A","distance_km":90,"energy_kwh":18}]` | `[('A', 5.0)]` |
| 4 | `trips=[{"vehicle_id":"B","distance_km":100,"energy_kwh":10},{"vehicle_id":"A","distance_km":100,"energy_kwh":10}]` | `[('A', 10.0), ('B', 10.0)]` |
| 5 | `trips=[{"vehicle_id":"A","distance_km":1,"energy_kwh":3},{"vehicle_id":"B","distance_km":10,"energy_kwh":1}]` | `[('B', 10.0), ('A', 0.33)]` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, lists of dictionaries, comprehensions, sorting, and arithmetic.

### Rules and Constraints
- Aggregate before dividing.
- Do not mutate input records.
- Empty input or all filtered records returns `[]`.

### Hints
1. Filter before mapping values.
2. Use a dictionary for per-vehicle totals.
3. Sort with a two-part key.

### Common Mistakes
- Averaging per-trip efficiencies instead of aggregating totals.
- Sorting ascending by accident.
- Losing deterministic tie ordering.

### Extension Challenge
Return total distance and total energy alongside each efficiency.
