# 24 - Regular Expressions and Structured Text Parsing Diagnostic Log - Easy

## Question Details
- **Concept:** Regular expressions and structured text parsing
- **Supporting Python concepts:** Named groups, validation, dictionaries
- **Difficulty:** Easy
- **Domain:** Offline diagnostic log parsing
- **Learning Objective:** Parse a strict structured log line with named regular-expression groups.
- **Estimated completion time:** 50 minutes

## Scenario
A test harness stores diagnostic events as lines such as `2026-08-26T14:05:07Z|P0420|WARNING|catalyst`.

## Function Details
Implement `parse_diagnostic_log(line: str) -> dict[str, str]`.

**Required API / operation:** Extract the timestamp, code, severity, and message from one valid line.

**Input rules and constraints:** The exact format is `YYYY-MM-DDTHH:MM:SSZ|CODE|SEVERITY|MESSAGE`. Code is 2 to 8 uppercase letters, digits, or hyphens. Severity is `INFO`, `WARNING`, or `CRITICAL`; message is non-empty and contains no pipe.

**Behavior and return shape:** Return keys `timestamp`, `code`, `severity`, and `message` with the captured text unchanged except for no surrounding whitespace.

**Implementation rules:** Use `re.fullmatch` or an equivalent anchored pattern. Raise `ValueError` for any malformed line. Treat the text as offline sample data.

## Tasks to Implement
1. Parse a strict structured log line with named regular-expression groups.
2. Extract the timestamp, code, severity, and message from one valid line.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `line="2026-08-26T14:05:07Z\|P0420\|WARNING\|catalyst"` | `{'timestamp': '2026-08-26T14:05:07Z', 'code': 'P0420', 'severity': 'WARNING', 'message': 'catalyst'}` |
| 2 | `line="2000-01-01T00:00:00Z\|A1\|INFO\|ready"` | `{'timestamp': '2000-01-01T00:00:00Z', 'code': 'A1', 'severity': 'INFO', 'message': 'ready'}` |
| 3 | `line="2024-02-29T23:59:59Z\|P-1\|CRITICAL\|engine fault"` | `{'timestamp': '2024-02-29T23:59:59Z', 'code': 'P-1', 'severity': 'CRITICAL', 'message': 'engine fault'}` |
| 4 | `line="2026-12-31T12:30:45Z\|AB12\|WARNING\|high temperature"` | `{'timestamp': '2026-12-31T12:30:45Z', 'code': 'AB12', 'severity': 'WARNING', 'message': 'high temperature'}` |
| 5 | `line="2026-08-26T14:05:07Z\|P0420\|INFO\|message with spaces"` | `{'timestamp': '2026-08-26T14:05:07Z', 'code': 'P0420', 'severity': 'INFO', 'message': 'message with spaces'}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, dictionaries, regular expressions, and exceptions.

### Rules and Constraints
- Use `re.fullmatch` or an equivalent anchored pattern.
- Raise `ValueError` for any malformed line.
- Treat the text as offline sample data.

### Hints
1. Capture each field with named groups.
2. Anchor the entire expression with `fullmatch`.
3. Make the message pattern reject the pipe character.

### Common Mistakes
- Using `search` and accepting trailing garbage.
- Making the message optional.
- Splitting on every pipe without validating the schema.

### Extension Challenge
Parse a batch of lines and return only events with `CRITICAL` severity.
