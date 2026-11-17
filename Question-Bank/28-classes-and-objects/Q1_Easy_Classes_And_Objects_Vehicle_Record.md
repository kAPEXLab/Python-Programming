# 28 - Classes and Objects Vehicle Record - Easy

## Question Details
- **Concept:** Classes and objects
- **Supporting Python concepts:** Attributes, instance state, methods
- **Difficulty:** Easy
- **Domain:** Offline vehicle record modeling
- **Learning Objective:** Model one vehicle as an object with state and a behavior method.
- **Estimated completion time:** 50 minutes

## Scenario
An inventory simulator needs a small object representing a vehicle and its current mileage.

## Function Details
Implement class `VehicleRecord` with attributes `vin: str`, `model: str`, `odometer_km: float` and method `summary(self) -> str`.

**Required API / operation:** Create a vehicle record object that can report its identity and mileage band.

**Input rules and constraints:** VIN is a 17-character valid VIN, model is non-empty, and odometer is from 0 through 2,000,000 km.

**Behavior and return shape:** `summary()` returns `MODEL | VIN | ODOMETER km`, with odometer rounded to one decimal. Construct invalid objects by raising `ValueError`.

**Implementation rules:** Store values on the instance. Do not connect to inventory services. Preserve the VIN exactly after uppercase normalization.

## Tasks to Implement
1. Model one vehicle as an object with state and a behavior method.
2. Create a vehicle record object that can report its identity and mileage band.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `VehicleRecord("1HGCM82633A004352", "Civic", 0).summary()` | `'Civic \| 1HGCM82633A004352 \| 0.0 km'` |
| 2 | `VehicleRecord("1HGCM82633A004352", "Civic", 12345.67).summary()` | `'Civic \| 1HGCM82633A004352 \| 12345.7 km'` |
| 3 | `VehicleRecord("1M8GDM9AXKP042788", "Van", 2000000).summary()` | `'Van \| 1M8GDM9AXKP042788 \| 2000000.0 km'` |
| 4 | `VehicleRecord("1HGCM82633A004352", "Model X", 10.26).summary()` | `'Model X \| 1HGCM82633A004352 \| 10.3 km'` |
| 5 | `VehicleRecord("1HGCM82633A004352", "EV", 1.04).summary()` | `'EV \| 1HGCM82633A004352 \| 1.0 km'` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Variables, strings, dictionaries, functions, and basic classes.

### Rules and Constraints
- Store values on the instance.
- Do not connect to inventory services.
- Preserve the VIN exactly after uppercase normalization.

### Hints
1. Validate constructor arguments.
2. Assign instance attributes with `self`.
3. Build the summary using an f-string.

### Common Mistakes
- Using class attributes for per-vehicle data.
- Omitting VIN validation.
- Returning a tuple instead of the required string.

### Extension Challenge
Add a method that returns `LOW`, `MEDIUM`, or `HIGH` mileage bands.
