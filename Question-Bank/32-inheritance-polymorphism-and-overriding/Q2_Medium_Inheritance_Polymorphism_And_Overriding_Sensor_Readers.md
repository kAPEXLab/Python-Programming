# 32 - Inheritance Polymorphism and Overriding Sensor Readers - Medium

## Question Details
- **Concept:** Inheritance, polymorphism, and method overriding
- **Supporting Python concepts:** Class design, numeric validation, formatting, type hints
- **Difficulty:** Medium
- **Domain:** Offline sensor reader normalization
- **Learning Objective:** Build interchangeable sensor readers whose overridden methods normalize different raw units.
- **Estimated completion time:** 55 minutes

## Scenario
A test bench receives raw values from temperature, pressure, and speed sensors. Each reader must expose the same interface while applying its own conversion.

## Function Details
Temperature converts Celsius to Fahrenheit using `c * 9 / 5 + 32`; pressure converts kPa to psi using `kpa * 0.1450377`; speed converts km/h to m/s using `kmh / 3.6`. Round each result to two decimal places.

**Required API / operation:** Create `SensorReader` with `read(raw_value: float) -> float`, then implement `TemperatureReader`, `PressureReader`, and `SpeedReader`. Add `read_all(readers: list[SensorReader], values: list[float]) -> list[float]`.

**Input rules and constraints:** Both lists must have equal nonzero length. Raw values must be finite numbers. Temperature is in Celsius, pressure in kPa, and speed in km/h.

**Behavior and return shape:** Return normalized values in reader order, rounded to two decimal places.

**Implementation rules:** `read_all` must call `read` polymorphically. Raise `ValueError` for invalid list lengths or non-finite values. No hardware, network, or external packages.

## Tasks to Implement
1. Build interchangeable sensor readers whose overridden methods normalize different raw units.
2. Create `SensorReader` with `read(raw_value: float) -> float`, then implement `TemperatureReader`, `PressureReader`, and `SpeedReader`. Add `read_all(readers: list[SensorReader], values: list[float]) -> list[float]`.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `read_all([TemperatureReader()], [0])` | `[32.0]` |
| 2 | `read_all([TemperatureReader()], [-40])` | `[-40.0]` |
| 3 | `read_all([PressureReader()], [100])` | `[14.5]` |
| 4 | `read_all([SpeedReader()], [36])` | `[10.0]` |
| 5 | `read_all([TemperatureReader(), PressureReader(), SpeedReader()], [20, 101.325, 3.6])` | `[68.0, 14.7, 1.0]` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, inheritance, methods, exceptions, and floating-point arithmetic.

### Rules and Constraints
- `read_all` must call `read` polymorphically.
- Raise `ValueError` for invalid list lengths or non-finite values.
- No hardware, network, or external packages.

### Hints
Validate shared input requirements before dispatching to reader methods.

### Common Mistakes
- Applying one conversion to every reader.
- Rounding before conversion.
- Matching readers by class name.

### Extension Challenge
Add a voltage reader that converts millivolts to volts.
