# 37 - Formatting Partial Vehicle Records - Medium

## Question Details
- **Concept:** Built-in exceptions and try-except
- **Supporting Python concepts:** Dictionaries, `KeyError`, `TypeError`, defaults, validation
- **Difficulty:** Medium
- **Domain:** Offline vehicle record lookup
- **Learning Objective:** Use targeted exception handling when reading optional and required vehicle fields.

## Scenario
A report generator reads partial vehicle dictionaries from a simulated archive.

## Function Details
- **Required Python interface:** Implement `vehicle_label(record: dict[str, object]) -> str`. Read required `vehicle_id` and optional `model_year`, defaulting a missing year to `"unknown"`.
- **Behavior:** Return `vehicle_id (year)` as text. Missing required ID raises `KeyError`; invalid ID or year types raise `TypeError`.
- **Return shape:** Return exact format such as `EV-1 (2026)` or `EV-1 (unknown)`.
- **Input rules and constraints:** IDs are non-empty strings. A supplied model year is an integer from 1886 through 2100. Additional constraints: Handle only the optional field's `KeyError` as a default; Do not catch and suppress missing required fields; Records are offline dictionaries.

## Tasks to Implement
1. Implement the specified Python interface: Implement `vehicle_label(record: dict[str, object]) -> str`. Read required `vehicle_id` and optional `model_year`, defaulting a missing year to `"unknown"`.
2. Apply the stated input validation and constraints: IDs are non-empty strings. A supplied model year is an integer from 1886 through 2100.
3. Implement the required behavior: Return `vehicle_id (year)` as text. Missing required ID raises `KeyError`; invalid ID or year types raise `TypeError`.
4. Return the specified result shape without changing the required ordering or formatting: Return exact format such as `EV-1 (2026)` or `EV-1 (unknown)`.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `vehicle_label({"vehicle_id": "EV-1", "model_year": 2026})` | `"EV-1 (2026)"` |
| 2 | `vehicle_label({"vehicle_id": "EV-2"})` | `"EV-2 (unknown)"` |
| 3 | `vehicle_label({"vehicle_id": "EV-3", "model_year": 2025})` | `"EV-3 (2025)"` |
| 4 | `vehicle_label({"vehicle_id": "EV-3", "model_year": 1886})` | `"EV-3 (1886)"` |
| 5 | `vehicle_label({"vehicle_id": "EV-4", "model_year": 2100})` | `"EV-4 (2100)"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Dictionaries, functions, `try-except`, and basic type checks.

### Rules and Constraints

- Handle only the optional field's `KeyError` as a default.
- Do not catch and suppress missing required fields.
- Records are offline dictionaries.

### Hints

Use a narrow `try` block around only the optional dictionary lookup.

### Common Mistakes

- Returning an empty ID.
- Catching `Exception` broadly.
- Treating string years as integers.

### Extension Challenge

Add optional `trim` text with a separate default.
