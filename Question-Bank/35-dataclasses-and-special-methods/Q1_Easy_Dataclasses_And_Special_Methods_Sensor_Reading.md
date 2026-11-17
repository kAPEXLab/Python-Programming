# 35 - Averaging Immutable Sensor Readings - Easy

## Question Details
- **Concept:** Dataclasses and special methods
- **Supporting Python concepts:** Frozen records, validation, ordering, representation
- **Difficulty:** Easy
- **Domain:** Offline sensor reading records
- **Learning Objective:** Use a dataclass to model immutable, comparable sensor readings.

## Scenario
A test harness stores normalized sensor readings that must be safe to compare and reuse.

## Function Details
- **Required Python interface:** Define frozen dataclass `SensorReading` with fields `sensor: str`, `value: float`, and `unit: str`. Implement `average_reading(readings: list[SensorReading]) -> SensorReading`.
- **Behavior:** Validate non-empty sensor and unit names and finite values. Average readings only when all sensor and unit fields match; return a new reading rounded to two decimals.
- **Return shape:** Return the average record with the shared sensor and unit.
- **Input rules and constraints:** The list must be non-empty. All readings must use the same sensor and unit. Additional constraints: Make the dataclass immutable; Equality must compare all fields through dataclass behavior; Raise `ValueError` for incompatible or invalid input.

## Tasks to Implement
1. Implement the specified Python interface: Define frozen dataclass `SensorReading` with fields `sensor: str`, `value: float`, and `unit: str`. Implement `average_reading(readings: list[SensorReading]) -> SensorReading`.
2. Apply the stated input validation and constraints: The list must be non-empty. All readings must use the same sensor and unit.
3. Implement the required behavior: Validate non-empty sensor and unit names and finite values. Average readings only when all sensor and unit fields match; return a new reading rounded to two decimals.
4. Return the specified result shape without changing the required ordering or formatting: Return the average record with the shared sensor and unit.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `[SensorReading("temp", 10.0, "C"), SensorReading("temp", 20.0, "C")]` | `SensorReading(sensor='temp', value=15.0, unit='C')` |
| 2 | `[SensorReading("speed", 0.0, "km/h")]` | `SensorReading(sensor='speed', value=0.0, unit='km/h')` |
| 3 | `[SensorReading("voltage", 12.346, "V"), SensorReading("voltage", 12.346, "V")]` | `SensorReading(sensor='voltage', value=12.35, unit='V')` |
| 4 | `[SensorReading("temp", -50.0, "C"), SensorReading("temp", 50.0, "C")]` | `SensorReading(sensor='temp', value=0.0, unit='C')` |
| 5 | `[SensorReading("pressure", 2.4, "bar"), SensorReading("pressure", 2.6, "bar"), SensorReading("pressure", 2.5, "bar")]` | `SensorReading(sensor='pressure', value=2.5, unit='bar')` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Classes, dataclasses, tuples, validation, and sorting.

### Rules and Constraints

- Make the dataclass immutable.
- Equality must compare all fields through dataclass behavior.
- Raise `ValueError` for incompatible or invalid input.

### Hints

Use `@dataclass(frozen=True)` and validate in `__post_init__`.

### Common Mistakes

- Mutating a frozen instance.
- Averaging records with different units.
- Returning a mutable dictionary.

### Extension Challenge

Add ordering by timestamp with a second dataclass field.
