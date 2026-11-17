# 38 - Resolving Charging-State Conflicts - Difficult

## Question Details
- **Concept:** Raising and defining custom exceptions
- **Supporting Python concepts:** Exception chaining, state validation, domain rules, type hints
- **Difficulty:** Difficult
- **Domain:** Offline charging-state conflict detection
- **Learning Objective:** Raise a meaningful custom exception when mutually exclusive charging states are requested.

## Scenario
A simulator receives charging commands from two independent scheduling sources.

## Function Details
- **Required Python interface:** Define `ChargingConflict(Exception)` and implement `resolve_charging_request(request: dict[str, object]) -> str`.
- **Behavior:** The request must contain `mode` (`AC`, `DC`, or `OFF`) and `scheduled` (`bool`). `DC` with `scheduled=True` raises `ChargingConflict`; `OFF` returns `DISABLED`; all other valid states return `READY`.
- **Return shape:** Return `READY` or `DISABLED` exactly, or raise the specified exception.
- **Input rules and constraints:** Mode must be an exact uppercase string and scheduled must be boolean. Missing fields should be reported as `KeyError`. Additional constraints: Include both conflicting fields in the custom exception message; Preserve `KeyError` for missing required fields; Keep all behavior offline.

## Tasks to Implement
1. Implement the specified Python interface: Define `ChargingConflict(Exception)` and implement `resolve_charging_request(request: dict[str, object]) -> str`.
2. Apply the stated input validation and constraints: Mode must be an exact uppercase string and scheduled must be boolean. Missing fields should be reported as `KeyError`.
3. Implement the required behavior: The request must contain `mode` (`AC`, `DC`, or `OFF`) and `scheduled` (`bool`). `DC` with `scheduled=True` raises `ChargingConflict`; `OFF` returns `DISABLED`; all other valid states return `READY`.
4. Return the specified result shape without changing the required ordering or formatting: Return `READY` or `DISABLED` exactly, or raise the specified exception.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `resolve_charging_request({"mode": "AC", "scheduled": True})` | `"READY"` |
| 2 | `resolve_charging_request({"mode": "DC", "scheduled": False})` | `"READY"` |
| 3 | `resolve_charging_request({"mode": "OFF", "scheduled": False})` | `"DISABLED"` |
| 4 | `resolve_charging_request({"mode": "OFF", "scheduled": True})` | `"DISABLED"` |
| 5 | `resolve_charging_request({"mode": "AC", "scheduled": False})` | `"READY"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Custom exceptions, dictionaries, boolean logic, and exception chaining.

### Rules and Constraints

- Include both conflicting fields in the custom exception message.
- Preserve `KeyError` for missing required fields.
- Keep all behavior offline.

### Hints

Extract required fields before applying the domain conflict rule.

### Common Mistakes

- Treating `1` as boolean `True`.
- Returning a normal status for a conflict.
- Hiding missing keys behind defaults.

### Extension Challenge

Chain a lower-level parsing error into `ChargingConflict`.
