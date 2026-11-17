# 41 - Managing a Diagnostic Session - Difficult

## Question Details
- **Concept:** Context managers
- **Supporting Python concepts:** Nested resources, transaction-like cleanup, validation, exception propagation
- **Difficulty:** Difficult
- **Domain:** Offline diagnostic session lifecycle
- **Learning Objective:** Coordinate session start and end states reliably with a context manager.

## Scenario
A simulated diagnostic session records commands only while the session is active.

## Function Details
- **Required Python interface:** Implement `DiagnosticSession(vehicle_id: str)` with `__enter__`, `__exit__`, `send(command: str) -> str`, and `commands() -> tuple[str, ...]`.
- **Behavior:** Entering starts the session. `send` accepts non-empty uppercase commands and returns `ACK:<command>`. Exiting ends the session and freezes the command history. Body exceptions must propagate.
- **Return shape:** Return acknowledgements from `send`; after exit, `commands()` returns an immutable tuple in order.
- **Input rules and constraints:** Vehicle ID and commands are non-empty strings. Commands must match uppercase letters, digits, and underscores only. Additional constraints: Sending before entry or after exit raises `RuntimeError`; Invalid commands raise `ValueError` without being recorded; This is an offline simulation and must not open a vehicle connection.

## Tasks to Implement
1. Implement the specified Python interface: Implement `DiagnosticSession(vehicle_id: str)` with `__enter__`, `__exit__`, `send(command: str) -> str`, and `commands() -> tuple[str, ...]`.
2. Apply the stated input validation and constraints: Vehicle ID and commands are non-empty strings. Commands must match uppercase letters, digits, and underscores only.
3. Implement the required behavior: Entering starts the session. `send` accepts non-empty uppercase commands and returns `ACK:<command>`. Exiting ends the session and freezes the command history. Body exceptions must propagate.
4. Return the specified result shape without changing the required ordering or formatting: Return acknowledgements from `send`; after exit, `commands()` returns an immutable tuple in order.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `with DiagnosticSession("EV-1") as session: ack = session.send("SCAN"); inspect commands() after exit` | `("ACK:SCAN", ("SCAN",))` |
| 2 | `with DiagnosticSession("EV-2") as session: a = session.send("READ_01"); b = session.send("CLEAR_02"); inspect commands() after exit` | `(("ACK:READ_01", "ACK:CLEAR_02"), ("READ_01", "CLEAR_02"))` |
| 3 | `with DiagnosticSession("EV-3") as session: ack = session.send("A1"); inspect commands() after exit` | `("ACK:A1", ("A1",))` |
| 4 | `with DiagnosticSession("EV-4") as session: pass; inspect commands() after exit` | `()` |
| 5 | `with DiagnosticSession("EV-5") as session: ack = session.send("CHECK_123"); inspect commands() after exit` | `("ACK:CHECK_123", ("CHECK_123",))` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Context-manager protocol, classes, lists, exceptions, and state machines.

### Rules and Constraints

- Sending before entry or after exit raises `RuntimeError`.
- Invalid commands raise `ValueError` without being recorded.
- This is an offline simulation and must not open a vehicle connection.

### Hints

Use a private mutable list during the session and expose a tuple afterward.

### Common Mistakes

- Recording invalid commands.
- Allowing commands after exit.
- Suppressing exceptions in `__exit__`.

### Extension Challenge

Add a maximum session duration supplied as a deterministic integer limit.
