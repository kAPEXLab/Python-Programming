# 16 - Fault Summary - Medium

## Question Details
- Concept: Dictionary and set comprehensions
- Supporting concepts: Nested records, filtering, normalization, validation
- Difficulty: Medium
- Domain: Offline diagnostic fault summary
- Learning Objective: Use comprehensions to build a code-to-count summary from diagnostic records.

## Scenario
A simulated scan returns records containing a fault code and severity.

## Function Details
- Function signature: `summarize_critical_faults(records: list[dict[str, str]]) -> dict[str, object]`
- Behavior / return shape: Count only critical faults and collect their normalized codes.
- Exact accepted inputs: Each record has non-empty `code` and `severity`. Severity is `INFO`, `WARNING`, or `CRITICAL`, case-insensitive. Codes use letters, digits, and hyphens.
- Output and validation / behavior: Return `counts` as a dictionary comprehension mapping each critical code to its count, and `codes` as a set comprehension of those codes. Normalize codes to uppercase.

## Tasks to Implement
1. Implement `summarize_critical_faults` with the exact signature above and validate the inputs against these accepted rules: Each record has non-empty `code` and `severity`. Severity is `INFO`, `WARNING`, or `CRITICAL`, case-insensitive. Codes use letters, digits, and hyphens.
2. Count only critical faults and collect their normalized codes.
3. Implement this output contract exactly: Return `counts` as a dictionary comprehension mapping each critical code to its count, and `codes` as a set comprehension of those codes. Normalize codes to uppercase.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | summarize_critical_faults([{"code": "F1", "severity": "CRITICAL"}]) | {"counts": {"F1": 1}, "codes": {"F1"}} | Typical valid input. |
| 2 | summarize_critical_faults([{"code": "F1", "severity": "CRITICAL"}, {"code": "F1", "severity": "critical"}]) | {"counts": {"F1": 2}, "codes": {"F1"}} | Valid boundary case. |
| 3 | summarize_critical_faults([{"code": "A", "severity": "INFO"}, {"code": "B", "severity": "WARNING"}]) | {"counts": {}, "codes": set()} | Checks the threshold rule. |
| 4 | summarize_critical_faults([{"code": "x-1", "severity": "CRITICAL"}, {"code": "Y2", "severity": "CRITICAL"}]) | {"counts": {"X-1": 1, "Y2": 1}, "codes": {"X-1", "Y2"}} | Checks an alternate valid shape. |
| 5 | summarize_critical_faults([{"code": "P1", "severity": "critical"}, {"code": "P2", "severity": "CRITICAL"}, {"code": "P1", "severity": "INFO"}]) | {"counts": {"P1": 1, "P2": 1}, "codes": {"P1", "P2"}} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of summarize_critical_faults that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Dictionaries, sets, comprehensions, strings, and functions.

### Rules and Constraints
- Invalid records raise ValueError.
- Preserve no ordering requirement for the set, but counts must be exact.
- Do not mutate input.

### Hints
1. Normalize records before building result comprehensions.
2. Count critical code occurrences in a temporary structure if needed.
3. A set comprehension naturally removes duplicate codes.

### Common Mistakes
- Counting warnings as critical.
- Leaving code case unchanged.
- Building the set from all records.

### Extension Challenge
Return a list of critical records sorted by descending code count.
