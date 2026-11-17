# 18 - Function Definition and Parameters Diagnostic Formatter - Difficult

## Question Details
- **Concept:** Function definitions with keyword-only parameters
- **Supporting Python concepts:** Strings, validation, formatting, defaults
- **Difficulty:** Difficult
- **Domain:** Offline diagnostic message formatting
- **Learning Objective:** Define a formatting function with a keyword-only detail flag and deterministic output.
- **Estimated completion time:** 50 minutes

## Scenario
A simulated diagnostic report needs compact or detailed messages for an operator.

## Function Details
Implement `format_diagnostic(code: str, severity: str, message: str, *, value: float | None = None, units: str = "", detailed: bool = False) -> str`.

**Required API / operation:** Format a normalized diagnostic message with optional measured value and units.

**Input rules and constraints:** Code is 2 to 12 alphanumeric or hyphen characters, severity is `INFO`, `WARNING`, or `CRITICAL`, and message is non-empty. If value is provided it is finite; units must be non-empty when value is provided. Detailed is boolean.

**Behavior and return shape:** Compact output is `[SEVERITY] CODE: MESSAGE`. Detailed output appends ` | value=VALUE UNITS` when value exists, with value rounded to two decimals and no trailing unit space.

**Implementation rules:** Normalize code and severity to uppercase and trim message. `value`, `units`, and `detailed` are keyword-only. Raise `ValueError` for invalid input; do not use external systems.

## Tasks to Implement
1. Define a formatting function with a keyword-only detail flag and deterministic output.
2. Format a normalized diagnostic message with optional measured value and units.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `code="p0420", severity="warning", message=" catalyst alert "` | `[WARNING] P0420: catalyst alert` |
| 2 | `code="B1", severity="INFO", message="Ready"` | `[INFO] B1: Ready` |
| 3 | `code="P0300", severity="CRITICAL", message="Misfire", detailed=True` | `[CRITICAL] P0300: Misfire` |
| 4 | `code="P0420", severity="WARNING", message="Catalyst", value=92.346, units="C", detailed=True` | `[WARNING] P0420: Catalyst \| value=92.35 C` |
| 5 | `code="AB-12", severity="INFO", message="Voltage", value=12, units="V", detailed=True` | `[INFO] AB-12: Voltage \| value=12.00 V` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, keyword arguments, strings, conditionals, and validation.

### Rules and Constraints
- Normalize code and severity to uppercase and trim message.
- `value`, `units`, and `detailed` are keyword-only.
- Raise `ValueError` for invalid input; do not use external systems.

### Hints
1. Normalize fields before assembling the string.
2. Check the value and units relationship together.
3. Use a conditional suffix for detailed measured data.

### Common Mistakes
- Allowing positional arguments after `*`.
- Adding a trailing space when units are absent.
- Rounding the message's source value in place.

### Extension Challenge
Add a keyword-only timestamp in integer milliseconds while preserving compact output.
