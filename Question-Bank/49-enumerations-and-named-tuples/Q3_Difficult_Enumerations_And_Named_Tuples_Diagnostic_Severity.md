# 49 - Parsing Typed Diagnostic Severity Events - Difficult

## Question Details
- **Concept:** Enums combined with named tuples
- **Supporting Python concepts:** Ordered severity, immutable records, parsing
- **Difficulty:** Difficult
- **Domain:** Offline diagnostic severity
- **Learning Objective:** Represent diagnostic events as immutable records with a controlled severity enum.

## Scenario
A report ranks synthetic diagnostic events without relying on arbitrary severity strings.

## Function Details
- **Required Python interface:** Define `Severity(IntEnum)` with `INFO=1`, `WARNING=2`, `CRITICAL=3`, and `DiagnosticEvent(NamedTuple)` with `code: str`, `severity: Severity`.
- **Behavior:** Implement `parse_event(code: str, severity: str) -> DiagnosticEvent`, normalizing severity and rejecting blank codes or unknown levels.
- **Return shape:** Return a `DiagnosticEvent` with the matching enum member.
- **Input rules and constraints:** Codes are non-empty strings; severity is `info`, `warning`, or `critical`, case-insensitive. Additional constraints: Use `IntEnum` for meaningful comparisons; Keep records immutable; Events are synthetic and offline.

## Tasks to Implement
1. Implement the specified Python interface: Define `Severity(IntEnum)` with `INFO=1`, `WARNING=2`, `CRITICAL=3`, and `DiagnosticEvent(NamedTuple)` with `code: str`, `severity: Severity`.
2. Apply the stated input validation and constraints: Codes are non-empty strings; severity is `info`, `warning`, or `critical`, case-insensitive.
3. Implement the required behavior: Implement `parse_event(code: str, severity: str) -> DiagnosticEvent`, normalizing severity and rejecting blank codes or unknown levels.
4. Return the specified result shape without changing the required ordering or formatting: Return a `DiagnosticEvent` with the matching enum member.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `parse_event("P0420", "info").severity` | `Severity.INFO` |
| 2 | `parse_event("U0100", "WARNING").severity` | `Severity.WARNING` |
| 3 | `parse_event("B0001", "critical").severity` | `Severity.CRITICAL` |
| 4 | `parse_event("C1234", " Info ").code` | `"C1234"` |
| 5 | `parse_event("P0301", "warning")` | `DiagnosticEvent(code='P0301', severity=<Severity.WARNING: 2>)` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Enums, named tuples, validation, and ordering.

### Rules and Constraints

- Use `IntEnum` for meaningful comparisons.
- Keep records immutable.
- Events are synthetic and offline.

### Hints

Use a normalized value-to-member mapping and validate the code separately.

### Common Mistakes

- Comparing unrelated strings for ranking.
- Mutating event fields.
- Treating `fatal` as an implicit alias.

### Extension Challenge

Add a function that returns the most severe event from an iterable.
