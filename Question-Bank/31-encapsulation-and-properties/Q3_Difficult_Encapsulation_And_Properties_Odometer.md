# 31 - Encapsulation and Properties Odometer - Difficult

## Question Details
- **Concept:** Encapsulation and properties
- **Supporting Python concepts:** Monotonic state, setters, invariants
- **Difficulty:** Difficult
- **Domain:** Offline odometer model
- **Learning Objective:** Enforce a non-decreasing odometer through an encapsulated property.
- **Estimated completion time:** 55 minutes

## Scenario
A simulator receives periodic odometer updates and must reject rollback values.

## Function Details
Implement class `Odometer` with property `kilometers: float` and method `add_distance(self, distance_km: float) -> float`.

**Required API / operation:** Create an odometer object whose reading can only increase or remain equal.

**Input rules and constraints:** Initial kilometers are 0 through 2,000,000. Added distance is from 0 through 5000 km. Values must be finite numbers, excluding booleans.

**Behavior and return shape:** The property and method return kilometers rounded to one decimal. `add_distance` increases the reading by the supplied distance.

**Implementation rules:** Store the backing value privately as `_kilometers`. Direct assignment may not reduce the reading; raise `ValueError` if it does. Do not connect to a real odometer.

## Tasks to Implement
1. Enforce a non-decreasing odometer through an encapsulated property.
2. Create an odometer object whose reading can only increase or remain equal.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `odometer=Odometer(0); odometer.kilometers` | `0.0` |
| 2 | `odometer=Odometer(10); odometer.add_distance(0)` | `10.0` |
| 3 | `odometer=Odometer(10); odometer.add_distance(0.05)` | `10.1` |
| 4 | `odometer=Odometer(1999999); odometer.add_distance(1)` | `2000000.0` |
| 5 | `odometer=Odometer(100); odometer.kilometers=100; odometer.kilometers` | `100.0` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, properties, comparisons, and exceptions.

### Rules and Constraints
- Store the backing value privately as `_kilometers`.
- Direct assignment may not reduce the reading; raise `ValueError` if it does.
- Do not connect to a real odometer.

### Hints
1. Validate the candidate assignment against the current value.
2. Let `add_distance` use the property setter or shared validation.
3. Permit equal assignments.

### Common Mistakes
- Allowing rollback values.
- Rejecting a zero-distance update.
- Rounding before comparing values.

### Extension Challenge
Track the number of accepted updates with a read-only property.
