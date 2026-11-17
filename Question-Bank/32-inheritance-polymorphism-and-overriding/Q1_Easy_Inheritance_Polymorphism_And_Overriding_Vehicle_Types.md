# 32 - Inheritance Polymorphism and Overriding Vehicle Types - Easy

## Question Details
- **Concept:** Inheritance, polymorphism, and method overriding
- **Supporting Python concepts:** Abstract behavior, type hints, dictionaries, deterministic formatting
- **Difficulty:** Easy
- **Domain:** Offline vehicle type reporting
- **Learning Objective:** Use a shared parent interface while allowing vehicle subclasses to provide specialized descriptions.
- **Estimated completion time:** 50 minutes

## Scenario
A fleet report needs one function that can describe several simulated vehicle types without checking every concrete class by name.

## Function Details
Implement `Vehicle`, `ElectricVehicle`, `HybridVehicle`, `ServiceVan`, and `build_vehicle_report(vehicles: list[Vehicle]) -> list[str]`. Use constructor signatures `(name: str, energy_units: float)` for the subclasses. Return strings in the form `name: category, range=NNN km`, rounded to the nearest whole kilometer.

**Required API / operation:** Create a base `Vehicle` class and subclasses for an electric vehicle, hybrid vehicle, and service van. Each subclass must override `category()` and `range_km()`.

**Input rules and constraints:** Names are non-empty strings. Energy units are non-negative. Electric range is `energy_units * 5`, hybrid range is `energy_units * 3`, and service-van range is `energy_units * 2`.

**Behavior and return shape:** Return one report string per input object, preserving order. Round ranges to whole kilometers using decimal half-up rounding, not Python's ties-to-even `round` behavior. Electric, hybrid, and service-van category values are respectively `"electric"`, `"hybrid"`, and `"service"`.

**Implementation rules:** The base class must define the public methods used polymorphically. Apply decimal half-up rounding wherever a range is rounded to a whole kilometer; do not use ties-to-even rounding. Do not use `isinstance` checks in the report function. Use Python 3.12+ and keep the simulation offline.

## Tasks to Implement
1. Use a shared parent interface while allowing vehicle subclasses to provide specialized descriptions.
2. Create a base `Vehicle` class and subclasses for an electric vehicle, hybrid vehicle, and service van. Each subclass must override `category()` and `range_km()`.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `build_vehicle_report([ElectricVehicle('EV', 10)])` | `['EV: electric, range=50 km']` |
| 2 | `build_vehicle_report([HybridVehicle('H', 10)])` | `['H: hybrid, range=30 km']` |
| 3 | `build_vehicle_report([ServiceVan('V', 10)])` | `['V: service, range=20 km']` |
| 4 | `build_vehicle_report([])` | `[]` |
| 5 | `build_vehicle_report([ElectricVehicle('E', 0.1)]) # half-up boundary` | `['E: electric, range=1 km']` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, instance methods, constructors, lists, and type hints.

### Rules and Constraints
- The base class must define the public methods used polymorphically.
- Apply decimal half-up rounding wherever a range is rounded to a whole kilometer; do not use ties-to-even rounding.
- Do not use `isinstance` checks in the report function.
- Use Python 3.12+ and keep the simulation offline.

### Hints
Define the common interface once, then override only the behavior that differs.

### Common Mistakes
- Calling subclass methods directly from the report function.
- Mutating the input list.
- Forgetting validation in constructors.

### Extension Challenge
Add a `HydrogenVehicle` subclass with a separate range rule.
