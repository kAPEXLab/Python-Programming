# 34 - Composition and Aggregation Vehicle Monitor - Easy

## Question Details
- **Concept:** Composition and aggregation
- **Supporting Python concepts:** Object ownership, delegation, validation, type hints
- **Difficulty:** Easy
- **Domain:** Offline vehicle monitor
- **Learning Objective:** Compose a monitor from sensor objects and delegate collection without exposing implementation details.
- **Estimated completion time:** 55 minutes

## Scenario
A simulated vehicle monitor owns a set of sensor objects and produces a snapshot for a test harness.

## Function Details
The monitor must aggregate each sensor once, reject duplicate names, and return values keyed by sensor name.

**Required API / operation:** Implement `Sensor(name: str, reading: float)` with `value() -> float`, where `value()` returns the stored reading, then implement `VehicleMonitor(sensors: list[Sensor])` with `snapshot() -> dict[str, float]`.

**Input rules and constraints:** Sensor names are non-empty and unique. Values must be finite numbers. The sensor list may be empty.

**Behavior and return shape:** Return a dictionary snapshot preserving sensor insertion order.

**Implementation rules:** The monitor owns the list supplied at construction by making a defensive copy. Do not hard-code sensor names. Raise `ValueError` for duplicate names or invalid values.

## Tasks to Implement
1. Compose a monitor from sensor objects and delegate collection without exposing implementation details.
2. Implement `Sensor(name: str, reading: float)` with `value() -> float`, where `value()` returns the stored reading, then implement `VehicleMonitor(sensors: list[Sensor])` with `snapshot() -> dict[str, float]`.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `VehicleMonitor([]).snapshot()` | `{}` |
| 2 | `VehicleMonitor([Sensor('speed', 0.0)]).snapshot()` | `{'speed': 0.0}` |
| 3 | `VehicleMonitor([Sensor('speed', 88.5), Sensor('voltage', 12.4)]).snapshot()` | `{'speed': 88.5, 'voltage': 12.4}` |
| 4 | `VehicleMonitor([Sensor('temp', -40.0)]).snapshot()` | `{'temp': -40.0}` |
| 5 | `VehicleMonitor([Sensor('soc', 100.0)]).snapshot()` | `{'soc': 100.0}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, constructors, methods, lists, and exceptions.

### Rules and Constraints
- The monitor owns the list supplied at construction by making a defensive copy.
- Do not hard-code sensor names.
- Raise `ValueError` for duplicate names or invalid values.

### Hints
Validate sensors while constructing the monitor, then delegate in `snapshot`.

### Common Mistakes
- Retaining a mutable caller list.
- Reading a sensor more than once.
- Silently overwriting duplicate names.

### Extension Challenge
Add a timestamp provider that labels each snapshot.
