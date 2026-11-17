# 50 - Validating Signals with a Descriptor - Easy

## Question Details
- **Concept:** Data descriptors
- **Supporting Python concepts:** `__get__`, `__set__`, validation, private storage
- **Difficulty:** Easy
- **Domain:** Offline signal validation
- **Learning Objective:** Use a descriptor to enforce a numeric signal range consistently across instances.

## Scenario
A simulated sensor model must reject impossible voltage readings at assignment time.

## Function Details
- **Required Python interface:** Implement `BoundedSignal(minimum: float, maximum: float)` and `BatterySignal` with `voltage = BoundedSignal(0.0, 20.0)`.
- **Behavior:** Store values per instance and raise `ValueError` for values outside the inclusive range or non-numeric values.
- **Return shape:** Reading the attribute returns the assigned float.
- **Input rules and constraints:** Voltage is a finite number from 0.0 through 20.0 volts; booleans are rejected even though they are integers in Python. Additional constraints: Implement descriptor methods rather than repeating property code; Require finite numeric values and reject booleans; Do not use class-level shared storage for values; This is not connected to a battery.

## Tasks to Implement
1. Implement the specified Python interface: Implement `BoundedSignal(minimum: float, maximum: float)` and `BatterySignal` with `voltage = BoundedSignal(0.0, 20.0)`.
2. Apply the stated input validation and constraints: Voltage is a finite number from 0.0 through 20.0 volts; booleans are rejected even though they are integers in Python.
3. Implement the required behavior: Store values per instance and raise `ValueError` for values outside the inclusive range or non-numeric values.
4. Return the specified result shape without changing the required ordering or formatting: Reading the attribute returns the assigned float.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `signal.voltage = 0.0; signal.voltage` | `0.0` |
| 2 | `signal.voltage = 20.0; signal.voltage` | `20.0` |
| 3 | `first.voltage = 12.5; second.voltage = 13.2; (first.voltage, second.voltage)` | `(12.5, 13.2)` |
| 4 | `signal.voltage = 7.0; signal.voltage` | `7.0` |
| 5 | `signal.voltage = 19.999; signal.voltage` | `19.999` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Classes, properties, descriptors, and exceptions.

### Rules and Constraints

- Implement descriptor methods rather than repeating property code.
- Require finite numeric values and reject booleans.
- Do not use class-level shared storage for values.
- This is not connected to a battery.

### Hints

Use a private instance attribute derived from the descriptor name.

### Common Mistakes

- Storing one value on the descriptor itself.
- Accepting booleans as measurements.
- Validating only on reads.

### Extension Challenge

Allow an optional unit label in the descriptor's constructor.
