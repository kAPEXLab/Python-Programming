# 25 - Data Validation Vehicle Sensor Packet - Easy

## Question Details
- **Concept:** Data validation
- **Supporting Python concepts:** Dictionaries, types, ranges, exceptions
- **Difficulty:** Easy
- **Domain:** Offline vehicle sensor packet validation
- **Learning Objective:** Validate a structured sensor packet before any calculation uses it.
- **Estimated completion time:** 45 minutes

## Scenario
A simulator receives a packet containing speed, battery voltage, and coolant temperature.

## Function Details
Implement `validate_sensor_packet(packet: dict[str, object]) -> dict[str, float]`.

**Required API / operation:** Return a normalized copy only when every required field is valid.

**Input rules and constraints:** Required keys are `speed_kmh` (0-300), `battery_voltage` (0-500), and `coolant_c` (-40-150). Values must be finite `int` or `float`, excluding booleans.

**Behavior and return shape:** Return the three fields as floats in the same units. Raise `ValueError` for missing, extra, mistyped, or out-of-range fields.

**Implementation rules:** Do not mutate the input. Reject extra keys to catch schema drift. This validates sample data only; it does not read sensors.

## Tasks to Implement
1. Validate a structured sensor packet before any calculation uses it.
2. Return a normalized copy only when every required field is valid.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `packet={'speed_kmh': 0, 'battery_voltage': 0, 'coolant_c': -40}` | `{'speed_kmh': 0.0, 'battery_voltage': 0.0, 'coolant_c': -40.0}` |
| 2 | `packet={'speed_kmh': 300, 'battery_voltage': 500, 'coolant_c': 150}` | `{'speed_kmh': 300.0, 'battery_voltage': 500.0, 'coolant_c': 150.0}` |
| 3 | `packet={'speed_kmh': 88.5, 'battery_voltage': 400.2, 'coolant_c': 90}` | `{'speed_kmh': 88.5, 'battery_voltage': 400.2, 'coolant_c': 90.0}` |
| 4 | `packet={'speed_kmh': 120, 'battery_voltage': 12.6, 'coolant_c': 20.5}` | `{'speed_kmh': 120.0, 'battery_voltage': 12.6, 'coolant_c': 20.5}` |
| 5 | `packet={'speed_kmh': 1, 'battery_voltage': 250, 'coolant_c': 0}` | `{'speed_kmh': 1.0, 'battery_voltage': 250.0, 'coolant_c': 0.0}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Dictionaries, functions, type checks, and exceptions.

### Rules and Constraints
- Do not mutate the input.
- Reject extra keys to catch schema drift.
- This validates sample data only; it does not read sensors.

### Hints
1. Compare the key set exactly.
2. Check numeric type before range checks.
3. Build a separate result dictionary.

### Common Mistakes
- Accepting missing fields as zero.
- Mutating the packet while normalizing it.
- Treating `True` as speed 1.

### Extension Challenge
Return a list of field-specific error strings instead of raising at the first error.
