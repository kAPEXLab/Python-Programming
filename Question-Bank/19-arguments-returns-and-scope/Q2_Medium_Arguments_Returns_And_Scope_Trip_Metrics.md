# 19 - Arguments Returns and Scope Trip Metrics - Medium

## Question Details
- **Concept:** Returning multiple values and local scope
- **Supporting Python concepts:** Iteration, validation, tuple returns, rounding
- **Difficulty:** Medium
- **Domain:** Simulated trip metrics
- **Learning Objective:** Return multiple calculated metrics while keeping all accumulators local to the function call.
- **Estimated completion time:** 35 minutes

## Scenario
An offline trip log stores distance in kilometers and energy consumed in kWh for each segment.

## Function Details
Implement `trip_metrics(segments: list[tuple[float, float]]) -> tuple[float, float, float | None]`.

**Required API / operation:** Calculate total distance, total energy, and consumption per 100 km.

**Input rules and constraints:** Each segment is `(distance_km, energy_kwh)` with distance from 0.0 through 1000.0 and energy from 0.0 through 500.0. The list has 0 through 100 segments; zero total distance is allowed only with zero energy.

**Behavior and return shape:** Return `(total_distance_km, total_energy_kwh, consumption_kwh_per_100km)`, with first two values and consumption rounded to two decimals. Consumption is `None` for zero distance.

**Implementation rules:** Return a tuple in exactly this order. Reject invalid segments with `ValueError`. A second call must not retain values from the first call.

## Tasks to Implement
1. Return multiple calculated metrics while keeping all accumulators local to the function call.
2. Calculate total distance, total energy, and consumption per 100 km.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `segments=[]` | `(0.0, 0.0, None)` |
| 2 | `segments=[(0.0, 0.0)]` | `(0.0, 0.0, None)` |
| 3 | `segments=[(100.0, 20.0)]` | `(100.0, 20.0, 20.0)` |
| 4 | `segments=[(50.0, 10.0), (50.0, 15.0)]` | `(100.0, 25.0, 25.0)` |
| 5 | `segments=[(1.25, 0.5), (2.75, 1.0)]` | `(4.0, 1.5, 37.5)` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, arguments, lists, loops, arithmetic, and tuples.

### Rules and Constraints
- Return a tuple in exactly this order.
- Reject invalid segments with `ValueError`.
- A second call must not retain values from the first call.

### Hints
1. Initialize totals inside the function.
2. Validate the zero-distance rule before computing the ratio.
3. Use a tuple return with explicit field order.

### Common Mistakes
- Using a persistent global total.
- Dividing energy by distance without multiplying by 100.
- Returning `0.0` instead of `None` for an empty trip.

### Extension Challenge
Return the most energy-intensive segment in a fourth value.
