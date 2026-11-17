# 13 - Diagnostic Result - Difficult

## Question Details
- Concept: Tuple packing and multiple unpacking
- Supporting concepts: Nested data, validation, status rules, functions
- Difficulty: Difficult
- Domain: Offline diagnostic result records
- Learning Objective: Unpack a diagnostic result, validate its fields, and repack a stable summary tuple.

## Scenario
An offline diagnostic tool reports (code, severity, passed, duration_ms) for a simulated check.

## Function Details
- Function signature: `normalize_diagnostic_result(result: tuple[str, str, bool, int]) -> tuple[str, str, str, int]`
- Behavior / return shape: Normalize a result for a deterministic report while preserving its essential status.
- Exact accepted inputs: `code` is 2 to 12 alphanumeric characters, case-insensitive after trimming whitespace; `severity` is `INFO`, `WARNING`, or `CRITICAL`, `passed` must be a boolean, and duration is an integer from 0 through 60,000 milliseconds.
- Output and validation / behavior: Return `(code, severity, outcome, duration_ms)`, where outcome is `"PASS"` when passed is true and `"FAIL"` otherwise. Normalize code and severity to uppercase after trimming whitespace.

## Tasks to Implement
1. Implement `normalize_diagnostic_result` with the exact signature above and validate the inputs against these accepted rules: `code` is 2 to 12 alphanumeric characters, case-insensitive after trimming whitespace; `severity` is `INFO`, `WARNING`, or `CRITICAL`, `passed` must be a boolean, and duration is an integer from 0 through 60,000 milliseconds.
2. Normalize a result for a deterministic report while preserving its essential status.
3. Implement this output contract exactly: Return `(code, severity, outcome, duration_ms)`, where outcome is `"PASS"` when passed is true and `"FAIL"` otherwise. Normalize code and severity to uppercase after trimming whitespace.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | normalize_diagnostic_result(("P1", "INFO", True, 0)) | ("P1", "INFO", "PASS", 0) | Typical valid input. |
| 2 | normalize_diagnostic_result((" ab12 ", "warning", False, 60000)) | ("AB12", "WARNING", "FAIL", 60000) | Valid boundary case. |
| 3 | normalize_diagnostic_result(("CRIT99", "CRITICAL", True, 100)) | ("CRIT99", "CRITICAL", "PASS", 100) | Checks the threshold rule. |
| 4 | normalize_diagnostic_result(("xy", "info", False, 1)) | ("XY", "INFO", "FAIL", 1) | Checks an alternate valid shape. |
| 5 | normalize_diagnostic_result(("Diag42", "WARNING", True, 30000)) | ("DIAG42", "WARNING", "PASS", 30000) | Checks uppercase normalization for a valid alphanumeric diagnostic code. |

## Expected Deliverables
- Complete implementation of normalize_diagnostic_result that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Tuple operations, strings, booleans, dictionaries, validation, and exceptions.

### Rules and Constraints
- Unpack all input fields in one statement.
- Validate before creating the output tuple.
- Reject malformed input with ValueError and do not mutate it.

### Hints
1. Strip and uppercase the string fields before checking choices.
2. Check isinstance(passed, bool) explicitly.
3. Pack the normalized values only after validation succeeds.

### Common Mistakes
- Treating any truthy value as a boolean.
- Losing the original diagnostic code.
- Returning a dictionary instead of the requested tuple.

### Extension Challenge
Return a named tuple-like structure that also includes a human-readable status message.
