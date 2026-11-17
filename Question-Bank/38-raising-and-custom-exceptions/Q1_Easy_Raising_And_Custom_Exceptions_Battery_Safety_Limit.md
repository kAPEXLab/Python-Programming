# 38 - Validating Battery Charge Requests - Easy

## Question Details
- **Concept:** Raising and defining custom exceptions
- **Supporting Python concepts:** Exception hierarchy, validation, type hints, numeric rules
- **Difficulty:** Easy
- **Domain:** Offline battery safety validation
- **Learning Objective:** Define and raise a domain-specific exception when a simulated battery request exceeds a safety limit.

## Scenario
A charging simulator must reject unsafe current requests before producing a plan.

## Function Details
- **Required Python interface:** Define `BatterySafetyLimit(Exception)` and implement `validate_charge_request(soc_percent: float, current_a: float) -> str`.
- **Behavior:** Return `ACCEPTED` when state of charge is 0 through 100 and current is 0 through 32 inclusive. Raise `BatterySafetyLimit` when current exceeds 32; raise `ValueError` for invalid SOC or negative current.
- **Return shape:** Return exactly `ACCEPTED` for valid requests.
- **Input rules and constraints:** Both inputs must be finite numbers. SOC is expected from 0 through 100. Additional constraints: The custom exception must carry the requested current and limit; Do not clamp unsafe current; This function never controls a charger.

## Tasks to Implement
1. Implement the specified Python interface: Define `BatterySafetyLimit(Exception)` and implement `validate_charge_request(soc_percent: float, current_a: float) -> str`.
2. Apply the stated input validation and constraints: Both inputs must be finite numbers. SOC is expected from 0 through 100.
3. Implement the required behavior: Return `ACCEPTED` when state of charge is 0 through 100 and current is 0 through 32 inclusive. Raise `BatterySafetyLimit` when current exceeds 32; raise `ValueError` for invalid SOC or negative current.
4. Return the specified result shape without changing the required ordering or formatting: Return exactly `ACCEPTED` for valid requests.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `validate_charge_request(0, 0)` | `"ACCEPTED"` |
| 2 | `validate_charge_request(50, 10)` | `"ACCEPTED"` |
| 3 | `validate_charge_request(100, 32)` | `"ACCEPTED"` |
| 4 | `validate_charge_request(25.5, 1.25)` | `"ACCEPTED"` |
| 5 | `validate_charge_request(75, 0)` | `"ACCEPTED"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Classes, functions, exceptions, and numeric validation.

### Rules and Constraints

- The custom exception must carry the requested current and limit.
- Do not clamp unsafe current.
- This function never controls a charger.

### Hints

Validate generic numeric constraints before raising the domain-specific exception.

### Common Mistakes

- Using `ValueError` for every failure.
- Silently reducing current.
- Accepting SOC above 100.

### Extension Challenge

Add a temperature input with a separate custom exception.
