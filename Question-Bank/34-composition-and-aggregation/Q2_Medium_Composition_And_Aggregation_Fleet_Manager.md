# 34 - Composition and Aggregation Fleet Manager - Medium

## Question Details
- **Concept:** Composition and aggregation
- **Supporting Python concepts:** Delegation, object collections, sorting, validation
- **Difficulty:** Medium
- **Domain:** Offline fleet manager
- **Learning Objective:** Aggregate independently managed vehicle objects into a deterministic fleet summary.
- **Estimated completion time:** 60 minutes

## Scenario
A fleet manager references vehicle records but does not own or clone them, allowing the same record to appear in other reports.

## Function Details
Return total mileage rounded to one decimal place. Rank summaries by mileage descending, then vehicle ID ascending.

**Required API / operation:** Implement `FleetVehicle(vehicle_id: str, mileage_km: float)` with `summary() -> str`, and `FleetManager(vehicles: list[FleetVehicle])` with `total_mileage() -> float` and `ranked_summaries() -> list[str]`.

**Input rules and constraints:** IDs are non-empty and unique. Mileage is from 0 through 2_000_000 km.

**Behavior and return shape:** `summary()` returns `ID: NNN.N km`; ranking returns those strings in sorted order.

**Implementation rules:** The manager aggregates references and must not mutate vehicle objects. Raise `ValueError` for duplicate IDs or invalid mileage. Use deterministic sorting.

## Tasks to Implement
1. Aggregate independently managed vehicle objects into a deterministic fleet summary.
2. Implement `FleetVehicle(vehicle_id: str, mileage_km: float)` with `summary() -> str`, and `FleetManager(vehicles: list[FleetVehicle])` with `total_mileage() -> float` and `ranked_summaries() -> list[str]`.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `FleetManager([]).total_mileage()` | `0.0` |
| 2 | `FleetManager([FleetVehicle('A', 0)]).ranked_summaries()` | `['A: 0.0 km']` |
| 3 | `FleetManager([FleetVehicle('B', 10.25), FleetVehicle('A', 10.25)]).ranked_summaries()` | `['A: 10.2 km', 'B: 10.2 km']` |
| 4 | `FleetManager([FleetVehicle('A', 100), FleetVehicle('B', 200)]).total_mileage()` | `300.0` |
| 5 | `FleetManager([FleetVehicle('MAX', 2000000)]).ranked_summaries()` | `['MAX: 2000000.0 km']` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, lists, dictionaries, sorting, and method calls.

### Rules and Constraints
- The manager aggregates references and must not mutate vehicle objects.
- Raise `ValueError` for duplicate IDs or invalid mileage.
- Use deterministic sorting.

### Hints
Use a sort key containing negative mileage and ID.

### Common Mistakes
- Sorting only by mileage and leaving ties unstable.
- Changing a vehicle's mileage while ranking.
- Treating aggregation as ownership.

### Extension Challenge
Add a method that returns only vehicles above a service threshold.
