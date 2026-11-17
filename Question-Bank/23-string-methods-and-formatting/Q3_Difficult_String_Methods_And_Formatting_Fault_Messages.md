# 23 - String Methods and Formatting Fault Messages - Difficult

## Question Details
- **Concept:** String methods and formatting
- **Supporting Python concepts:** Replacement, capitalization, templates
- **Difficulty:** Difficult
- **Domain:** Offline dashboard fault messages
- **Learning Objective:** Compose concise fault messages from normalized text fields.
- **Estimated completion time:** 35 minutes

## Scenario
A dashboard prototype converts a fault code, severity, and component into one consistent operator message.

## Function Details
Implement `build_fault_message(code: str, severity: str, component: str) -> str`.

**Required API / operation:** Normalize the fields and render a fixed message template.

**Input rules and constraints:** Code is 2 to 8 alphanumeric or hyphen characters. Severity is `info`, `warning`, or `critical`, case-insensitive. Component is non-empty text.

**Behavior and return shape:** Return `SEVERITY: CODE - Component requires attention`, where severity and code are uppercase and component uses trimmed title case.

**Implementation rules:** Collapse repeated whitespace in the component. Reject unsupported severity, malformed code, or empty component with `ValueError`. Do not print or connect to a dashboard.

## Tasks to Implement
1. Compose concise fault messages from normalized text fields.
2. Normalize the fields and render a fixed message template.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `code="p0420", severity="warning", component=" catalytic converter "` | `'WARNING: P0420 - Catalytic Converter requires attention'` |
| 2 | `code="B1", severity="INFO", component="battery"` | `'INFO: B1 - Battery requires attention'` |
| 3 | `code="C-12", severity="critical", component="front   left sensor"` | `'CRITICAL: C-12 - Front Left Sensor requires attention'` |
| 4 | `code="AB-2", severity="WARNING", component="  tire pressure  "` | `'WARNING: AB-2 - Tire Pressure requires attention'` |
| 5 | `code="P0300", severity="Info", component="engine mount"` | `'INFO: P0300 - Engine Mount requires attention'` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
String methods, f-strings, dictionaries, and validation.

### Rules and Constraints
- Collapse repeated whitespace in the component.
- Reject unsupported severity, malformed code, or empty component with `ValueError`.
- Do not print or connect to a dashboard.

### Hints
1. Normalize code and severity independently.
2. Use `split` and `join` before title-casing the component.
3. Validate severity using a set of allowed values.

### Common Mistakes
- Title-casing the fault code.
- Accepting arbitrary severity text.
- Treating whitespace as a component name.

### Extension Challenge
Allow an optional measured value and unit while keeping the original output unchanged when omitted.
