# 29 - Constructors Attributes and Instance Methods Fleet Vehicle - Difficult

## Question Details
- **Concept:** Constructors, attributes, and instance methods
- **Supporting Python concepts:** Counters, validation, formatted records
- **Difficulty:** Difficult
- **Domain:** Offline fleet vehicle trip tracking
- **Learning Objective:** Maintain per-object trip totals through validated instance methods.
- **Estimated completion time:** 55 minutes

## Scenario
A fleet simulator tracks total distance and trip count for each vehicle independently.

## Function Details
Implement class `FleetVehicle` with `__init__(self, vehicle_id: str)`, `record_trip(self, distance_km: float) -> None`, and `report(self) -> str`.

**Required API / operation:** Create a vehicle object that records completed trips.

**Input rules and constraints:** Vehicle ID is non-empty. Trip distance is finite and from 0.1 through 5000 km.

**Behavior and return shape:** `report()` returns `ID | trips=N | distance=NN.N km`, with distance rounded to one decimal.

**Implementation rules:** Initialize trip count and distance per instance. Reject invalid IDs and distances with `ValueError`. No trip is recorded if validation fails.

## Tasks to Implement
1. Maintain per-object trip totals through validated instance methods.
2. Create a vehicle object that records completed trips.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `vehicle=FleetVehicle("EV-1"); vehicle.report()` | `'EV-1 \| trips=0 \| distance=0.0 km'` |
| 2 | `vehicle=FleetVehicle("EV-2"); vehicle.record_trip(10); vehicle.report()` | `'EV-2 \| trips=1 \| distance=10.0 km'` |
| 3 | `vehicle=FleetVehicle("A"); vehicle.record_trip(0.1); vehicle.report()` | `'A \| trips=1 \| distance=0.1 km'` |
| 4 | `vehicle=FleetVehicle("B"); vehicle.record_trip(100.25); vehicle.record_trip(20.25); vehicle.report()` | `'B \| trips=2 \| distance=120.5 km'` |
| 5 | `vehicle=FleetVehicle("MAX"); vehicle.record_trip(5000); vehicle.report()` | `'MAX \| trips=1 \| distance=5000.0 km'` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, constructors, methods, numeric validation, and strings.

### Rules and Constraints
- Initialize trip count and distance per instance.
- Reject invalid IDs and distances with `ValueError`.
- No trip is recorded if validation fails.

### Hints
1. Set `trip_count = 0` and `total_distance_km = 0.0` in the constructor.
2. Validate before incrementing either value.
3. Format the report with one decimal place.

### Common Mistakes
- Sharing totals between vehicles.
- Incrementing the count for invalid trips.
- Rounding each trip before accumulation.

### Extension Challenge
Add average trip distance to the report.
