# 32 - Inheritance Polymorphism and Overriding Charging Strategies - Difficult

## Question Details
- **Concept:** Inheritance, polymorphism, and method overriding
- **Supporting Python concepts:** Encapsulation, validation, numeric rules, collections
- **Difficulty:** Difficult
- **Domain:** Offline charging schedule estimation
- **Learning Objective:** Represent charging algorithms behind one polymorphic strategy interface.
- **Estimated completion time:** 60 minutes

## Scenario
A simulator compares slow, fast, and solar-assisted charging plans without controlling a real charger.

## Function Details
Implement `estimate_plan(strategy: ChargingStrategy, energy_kwh: float) -> int` and `compare_strategies(strategies: list[ChargingStrategy], energy_kwh: float) -> list[int]`. Round each charging duration up to the next whole minute.

**Required API / operation:** Create `ChargingStrategy` with `estimate_minutes(energy_kwh: float) -> int`. Implement `SlowCharging`, `FastCharging`, and `SolarCharging` using rates of 3, 11, and 7 kW respectively. Solar charging adds a fixed 20-minute setup time.

**Input rules and constraints:** Energy must be from 0 through 120 kWh inclusive. Strategy lists must be non-empty.

**Behavior and return shape:** Return estimated minutes, with zero energy returning zero minutes. Solar's setup time applies only when energy is greater than zero.

**Implementation rules:** Dispatch through the shared method only. Raise `ValueError` for invalid energy or an empty strategy list. This is a deterministic offline estimate, not a charger command.

## Tasks to Implement
1. Represent charging algorithms behind one polymorphic strategy interface.
2. Create `ChargingStrategy` with `estimate_minutes(energy_kwh: float) -> int`. Implement `SlowCharging`, `FastCharging`, and `SolarCharging` using rates of 3, 11, and 7 kW respectively. Solar charging adds a fixed 20-minute setup time.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `estimate_plan(SlowCharging(), 0)` | `0` |
| 2 | `estimate_plan(SlowCharging(), 3)` | `60` |
| 3 | `estimate_plan(FastCharging(), 11)` | `60` |
| 4 | `estimate_plan(SolarCharging(), 7)` | `80` |
| 5 | `compare_strategies([SlowCharging(), FastCharging(), SolarCharging()], 1)` | `[20, 6, 29]` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, inheritance, method overriding, loops, and exception handling.

### Rules and Constraints
- Dispatch through the shared method only.
- Raise `ValueError` for invalid energy or an empty strategy list.
- This is a deterministic offline estimate, not a charger command.

### Hints
Compute the raw duration as energy divided by rate, then use ceiling.

### Common Mistakes
- Adding solar setup time at zero energy.
- Returning fractional minutes.
- Embedding strategy type checks in helper functions.

### Extension Challenge
Allow each strategy to report its name and produce a labeled comparison.
