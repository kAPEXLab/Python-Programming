# 42 - Logging Fleet Processing Results - Easy

## Question Details
- **Concept:** The `logging` module
- **Supporting Python concepts:** Log levels, handlers, formatted messages
- **Difficulty:** Easy
- **Domain:** Offline fleet processing
- **Learning Objective:** Configure a logger that records deterministic fleet-processing events at the requested severity.

## Scenario
A fleet processor needs useful offline logs while it summarizes incoming vehicle records.

## Function Details
- **Required Python interface:** Create `FleetProcessor(logger: logging.Logger)` with `process(vehicle_id: str, distance_km: float) -> str`.
- **Behavior:** Log an `INFO` message for a valid record and return `PROCESSED:<vehicle_id>:<distance_km:.1f>km`. Reject invalid identifiers or negative distances with `ValueError` and log an `ERROR` message.
- **Return shape:** Return the exact processed string. Logging text must include the vehicle identifier and use the appropriate level.
- **Input rules and constraints:** `vehicle_id` is a non-empty string. `distance_km` is a finite number from 0 through 2000 km. Additional constraints: Use the supplied logger; do not configure the root logger; Use Python 3.12+ and deterministic values; This is an offline simulation with no real vehicle connection.

## Tasks to Implement
1. Implement the specified Python interface: Create `FleetProcessor(logger: logging.Logger)` with `process(vehicle_id: str, distance_km: float) -> str`.
2. Apply the stated input validation and constraints: `vehicle_id` is a non-empty string. `distance_km` is a finite number from 0 through 2000 km.
3. Implement the required behavior: Log an `INFO` message for a valid record and return `PROCESSED:<vehicle_id>:<distance_km:.1f>km`. Reject invalid identifiers or negative distances with `ValueError` and log an `ERROR` message.
4. Return the specified result shape without changing the required ordering or formatting: Return the exact processed string. Logging text must include the vehicle identifier and use the appropriate level.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `processor.process("EV-1", 0.0); capture emitted record` | `("PROCESSED:EV-1:0.0km", INFO record whose message includes "EV-1")` |
| 2 | `processor.process("EV-2", 12.34); capture emitted record` | `("PROCESSED:EV-2:12.3km", INFO record whose message includes "EV-2")` |
| 3 | `processor.process("EV-3", 2000.0); capture emitted record` | `("PROCESSED:EV-3:2000.0km", INFO record whose message includes "EV-3")` |
| 4 | `processor.process("FLEET-7", 1500.56); capture emitted record` | `("PROCESSED:FLEET-7:1500.6km", INFO record whose message includes "FLEET-7")` |
| 5 | `processor.process("EV-5", 42.0); capture emitted record` | `("PROCESSED:EV-5:42.0km", INFO record whose message includes "EV-5")` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Functions, classes, strings, exceptions, and basic module imports.

### Rules and Constraints

- Use the supplied logger; do not configure the root logger.
- Use Python 3.12+ and deterministic values.
- This is an offline simulation with no real vehicle connection.

### Hints

Validate before logging success, and use a formatter-friendly message with arguments.

### Common Mistakes

- Calling `basicConfig` inside the class.
- Logging errors at `INFO` level.
- Rounding the input before validating it.

### Extension Challenge

Add a `WARNING` log when distance exceeds 1500 km.
