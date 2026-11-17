# 42 - Logging Charging Sessions - Medium

## Question Details
- **Concept:** Logger hierarchy and handlers
- **Supporting Python concepts:** `StringIO`, log capture, severity filtering
- **Difficulty:** Medium
- **Domain:** Offline charging service
- **Learning Objective:** Capture charging lifecycle messages with stable levels and a predictable logger configuration.

## Scenario
An offline charging service reports session start, completion, and rejected requests for a test harness.

## Function Details
- **Required Python interface:** Implement `ChargingService(logger: logging.Logger)` with `start_session(vehicle_id: str, target_soc: int) -> str`.
- **Behavior:** Log `INFO` for accepted starts, `WARNING` when the target is already reached, and `ERROR` for invalid input. Return `STARTED:<vehicle_id>:<target_soc>%` for accepted requests.
- **Return shape:** Return either the exact started string, `ALREADY_REACHED`, or raise `ValueError`.
- **Input rules and constraints:** `vehicle_id` is non-empty. `target_soc` is an integer from 1 through 100. A target below the current fixed simulated SOC of 80 is a warning and returns `ALREADY_REACHED`. Additional constraints: The logger must be named `charging.service` or be supplied by the caller; Do not write directly to stdout; Data and charging are simulated only.

## Tasks to Implement
1. Implement the specified Python interface: Implement `ChargingService(logger: logging.Logger)` with `start_session(vehicle_id: str, target_soc: int) -> str`.
2. Apply the stated input validation and constraints: `vehicle_id` is non-empty. `target_soc` is an integer from 1 through 100. A target below the current fixed simulated SOC of 80 is a warning and returns `ALREADY_REACHED`.
3. Implement the required behavior: Log `INFO` for accepted starts, `WARNING` when the target is already reached, and `ERROR` for invalid input. Return `STARTED:<vehicle_id>:<target_soc>%` for accepted requests.
4. Return the specified result shape without changing the required ordering or formatting: Return either the exact started string, `ALREADY_REACHED`, or raise `ValueError`.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `service.start_session("EV-1", 81) with simulated current SOC 80; capture record` | `("STARTED:EV-1:81%", INFO record)` |
| 2 | `service.start_session("EV-2", 100) with simulated current SOC 80; capture record` | `("STARTED:EV-2:100%", INFO record)` |
| 3 | `service.start_session("EV-3", 79) with simulated current SOC 80; capture record` | `("ALREADY_REACHED", WARNING record)` |
| 4 | `service.start_session("EV-4", 1) with simulated current SOC 80; capture record` | `("ALREADY_REACHED", WARNING record)` |
| 5 | `service.start_session("EV-5", 99) with simulated current SOC 80; capture record` | `("STARTED:EV-5:99%", INFO record)` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Logging basics, classes, context-free service methods, and string streams.

### Rules and Constraints

- The logger must be named `charging.service` or be supplied by the caller.
- Do not write directly to stdout.
- Data and charging are simulated only.

### Hints

Use one logger call per outcome and attach a temporary handler in tests.

### Common Mistakes

- Treating a warning as an exception.
- Accepting boolean values as SOC integers.
- Printing messages instead of logging them.

### Extension Challenge

Add a session identifier and include it in every log record.
