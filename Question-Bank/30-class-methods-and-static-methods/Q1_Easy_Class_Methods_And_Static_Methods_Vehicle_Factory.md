# 30 - Class Methods and Static Methods Vehicle Factory - Easy

## Question Details
- **Concept:** Class methods and static methods
- **Supporting Python concepts:** Alternate constructors, validation, class state
- **Difficulty:** Easy
- **Domain:** Offline vehicle object factory
- **Learning Objective:** Use a class method as an alternate constructor and a static method for shared validation.
- **Estimated completion time:** 55 minutes

## Scenario
A simulator creates vehicles from compact specification text such as `EV-1|sedan|2026`.

## Function Details
Implement class `VehicleFactory` with `from_spec(cls, spec: str) -> VehicleFactory` and static method `valid_year(year: int) -> bool`. Store `vehicle_id`, `kind`, and `year`.

**Required API / operation:** Parse the specification and construct a validated vehicle object.

**Input rules and constraints:** Spec has exactly three pipe-separated fields. ID is non-empty, kind is `sedan`, `suv`, or `truck`, and year is 2000 through 2100.

**Behavior and return shape:** `valid_year` returns a boolean. `from_spec` returns an instance with uppercase ID and lowercase kind.

**Implementation rules:** `from_spec` must call class construction through `cls`. Raise `ValueError` for malformed specifications. No registry or external factory service is used.

## Tasks to Implement
1. Use a class method as an alternate constructor and a static method for shared validation.
2. Parse the specification and construct a validated vehicle object.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `obj=VehicleFactory.from_spec('EV-1\|sedan\|2026'); (obj.vehicle_id, obj.kind, obj.year)` | `('EV-1', 'sedan', 2026)` |
| 2 | `VehicleFactory.valid_year(2000)` | `True` |
| 3 | `VehicleFactory.valid_year(2100)` | `True` |
| 4 | `obj=VehicleFactory.from_spec(' van-2 \|SUV\| 2024 '); (obj.vehicle_id, obj.kind, obj.year)` | `('VAN-2', 'suv', 2024)` |
| 5 | `VehicleFactory.valid_year(1999)` | `False` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, constructors, class methods, static methods, and exceptions.

### Rules and Constraints
- `from_spec` must call class construction through `cls`.
- Raise `ValueError` for malformed specifications.
- No registry or external factory service is used.

### Hints
1. Split and validate the field count.
2. Convert year only after checking text shape.
3. Use `@classmethod` and `@staticmethod` decorators.

### Common Mistakes
- Calling `VehicleFactory(...)` instead of `cls(...)`.
- Making `valid_year` depend on instance state.
- Accepting unknown vehicle kinds.

### Extension Challenge
Add a class counter for successfully created vehicles.
