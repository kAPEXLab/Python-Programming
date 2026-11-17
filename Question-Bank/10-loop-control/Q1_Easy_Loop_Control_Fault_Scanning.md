# 10 - Fault Scanning - Easy

## Question Details
- Concept: break
- Supporting concepts: Lists, strings, validation, searching
- Difficulty: Easy
- Domain: Diagnostic fault scanning
- Learning Objective: Use break to stop a scan at the first critical simulated fault.

## Scenario
A diagnostic scan checks DTC labels in order. CRITICAL means the scan should stop immediately; other labels are noncritical.

## Function Details
- Function signature: `find_first_critical(fault_levels: list[str]) -> int | None`
- Behavior / return shape: Return the index of the first critical fault, or None when none exists.
- Exact accepted inputs: List length is 0 through 10,000. Each label is `INFO`, `WARNING`, or `CRITICAL`, case-insensitive. Reject invalid values with `ValueError`.
- Output and validation / behavior: Return the zero-based index of the first `CRITICAL`, or `None`.

## Tasks to Implement
1. Implement `find_first_critical` with the exact signature above and validate the inputs against these accepted rules: List length is 0 through 10,000. Each label is `INFO`, `WARNING`, or `CRITICAL`, case-insensitive. Reject invalid values with `ValueError`.
2. Return the index of the first critical fault, or None when none exists.
3. Implement this output contract exactly: Return the zero-based index of the first `CRITICAL`, or `None`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | find_first_critical(["CRITICAL"]) | 0 | A critical fault at the first position. |
| 2 | find_first_critical(["INFO", "CRITICAL", "WARNING"]) | 1 | Stops at the first critical label. |
| 3 | find_first_critical(["INFO", "WARNING"]) | None | Returns None when no critical fault exists. |
| 4 | find_first_critical([]) | None | An empty valid list has no critical entry. |
| 5 | find_first_critical(["warning", "critical"]) | 1 | Matching is case-insensitive. |
## Expected Deliverables
- Complete implementation of find_first_critical that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, loops, conditionals, strings, and functions.

### Rules and Constraints
- Use break to stop after the first critical entry.
- Preserve input order.
- Do not use list.index() as a shortcut.

### Hints
1. Track the index with enumerate().
2. Break when the normalized label is critical.
3. Keep a result variable initialized to None.

### Common Mistakes
- Returning the last critical index.
- Continuing after the first critical fault.
- Forgetting empty input.

### Extension Challenge
Return the number of records inspected as well as the index.
