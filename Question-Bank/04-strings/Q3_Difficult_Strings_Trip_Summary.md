# 04 - Trip Summary - Difficult

## Question Details
- Concept: Strings, formatting, and structured text generation
- Supporting concepts: Dictionaries, lists, validation, aggregation
- Difficulty: Difficult
- Domain: Trip‑computer summary
- Learning Objective: Generate a stable multi‑line text report from structured trip data while handling validation and rounding.

---

## Scenario
Implement a function that receives a list of segment dictionaries and returns a formatted trip‑summary report.

## Function Details
- Function signature: `build_trip_summary(segments: list[dict[str, int | float]]) -> str`
- Behavior / return shape: Aggregate validated trip segments into the specified five-line summary, including total distance and fuel, fuel economy, mean segment speed, and the first longest-segment index.
- Exact accepted inputs: Accept 1–1,000 dictionaries. Each `distance_km` is a finite non-boolean number from 0 through 5,000 inclusive; each `fuel_liters` is a finite non-boolean number from 0 through 500 inclusive; each `average_speed_kmh` is a finite non-boolean number from 0 through 300 inclusive. Each dictionary must contain all three required keys. At least one distance must be positive. Raise `ValueError` for malformed data, invalid types, or out-of-range values. These bounds represent reasonable per-segment limits for a simulated vehicle trip.
- Output and validation / behavior: Return exactly five lines with two-decimal numeric formatting: Distance, Fuel, Economy (total fuel / total distance × 100, or 0 when total fuel is 0), Average segment speed (arithmetic mean), and Longest segment (first longest segment index, 1-based).

## Tasks to Implement
1. Implement `build_trip_summary` with the exact signature above. Validate that `segments` contains 1–1,000 dictionaries with all three required keys; `distance_km` is a finite, non-boolean number from 0 through 5,000, `fuel_liters` is a finite, non-boolean number from 0 through 500, and `average_speed_kmh` is a finite, non-boolean number from 0 through 300. Require at least one positive distance and raise `ValueError` for malformed or out-of-range values.
2. Aggregate validated trip segments into the specified five-line summary, including total distance and fuel, fuel economy, mean segment speed, and the first longest-segment index.
3. Implement this output contract exactly: Return exactly five lines with two-decimal numeric formatting: Distance, Fuel, Economy (total fuel / total distance × 100, or 0 when total fuel is 0), Average segment speed (arithmetic mean), and Longest segment (first longest segment index, 1-based).

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | build_trip_summary([{"distance_km": 100, "fuel_liters": 5, "average_speed_kmh": 60}]) | Distance: 100.00 km<br>Fuel: 5.00 L<br>Economy: 5.00 L/100km<br>Average segment speed: 60.00 km/h<br>Longest segment: 1 | Typical valid input. |
| 2 | build_trip_summary([{"distance_km": 10, "fuel_liters": 0, "average_speed_kmh": 0}, {"distance_km": 20, "fuel_liters": 1, "average_speed_kmh": 30}]) | Distance: 30.00 km<br>Fuel: 1.00 L<br>Economy: 3.33 L/100km<br>Average segment speed: 15.00 km/h<br>Longest segment: 2 | Valid lower or upper boundary. |
| 3 | build_trip_summary([{"distance_km": 50, "fuel_liters": 3, "average_speed_kmh": 80}, {"distance_km": 50, "fuel_liters": 2, "average_speed_kmh": 100}]) | Distance: 100.00 km<br>Fuel: 5.00 L<br>Economy: 5.00 L/100km<br>Average segment speed: 90.00 km/h<br>Longest segment: 1 | Checks the threshold rule. |
| 4 | build_trip_summary([{"distance_km": 0, "fuel_liters": 1, "average_speed_kmh": 25}, {"distance_km": 1, "fuel_liters": 0, "average_speed_kmh": 35}]) | Distance: 1.00 km<br>Fuel: 1.00 L<br>Economy: 100.00 L/100km<br>Average segment speed: 30.00 km/h<br>Longest segment: 2 | Checks a second valid shape or aggregate. |
| 5 | build_trip_summary([{"distance_km": 5000, "fuel_liters": 500, "average_speed_kmh": 300}]) | Distance: 5000.00 km<br>Fuel: 500.00 L<br>Economy: 10.00 L/100km<br>Average segment speed: 300.00 km/h<br>Longest segment: 1 | Confirms all three inclusive upper bounds are accepted. |

## Expected Deliverables
- Complete implementation of the required function that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Hints
1. Validate each segment before any aggregation.
2. Keep track of the longest distance and its **first** index (1‑based).
3. Economy = total_fuel / total_distance * 100 (0 when total fuel is 0).
4. Average speed = arithmetic mean of the average_speed_kmh values.
5. Use f‑strings with :.2f for formatting; do **not** round intermediate
totals.
