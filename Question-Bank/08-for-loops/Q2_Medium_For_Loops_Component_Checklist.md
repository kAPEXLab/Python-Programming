# 08 - Component Checklist - Medium

## Question Details
- Concept: for loops over collections
- Supporting concepts: Lists, strings, sets, validation, filtering
- Difficulty: Medium
- Domain: Manufacturing component inspection
- Learning Objective: Process an inspection checklist and identify incomplete or failed components.

## Scenario
A factory inspection records each component name and result. Valid results are PASS, FAIL, and SKIP.

## Function Details
- Function signature: `inspect_components(records: list[tuple[str, str]]) -> dict[str, object]`
- Behavior / return shape: Summarize the checklist while preserving the order in which failed components occurred.
- Exact accepted inputs: There are 0 to 10,000 records. Names are non-empty strings. Results are case-insensitive but must normalize to `PASS`, `FAIL`, or `SKIP`. Reject invalid records with `ValueError`.
- Output and validation / behavior: Return integer counts in `total`, `passed`, and `skipped`, plus `failed_components`, the failed names in input order.

## Tasks to Implement
1. Implement `inspect_components` with the exact signature above and validate the inputs against these accepted rules: There are 0 to 10,000 records. Names are non-empty strings. Results are case-insensitive but must normalize to `PASS`, `FAIL`, or `SKIP`. Reject invalid records with `ValueError`.
2. Summarize the checklist while preserving the order in which failed components occurred.
3. Implement this output contract exactly: Return integer counts in `total`, `passed`, and `skipped`, plus `failed_components`, the failed names in input order.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | inspect_components([["ECU", "PASS"]]) | {"total": 1, "passed": 1, "failed_components": [], "skipped": 0} | Typical valid input. |
| 2 | inspect_components([["ABS", "FAIL"], ["BMS", "SKIP"]]) | {"total": 2, "passed": 0, "failed_components": ["ABS"], "skipped": 1} | Counts a failure and skipped component while retaining the input name. |
| 3 | inspect_components([["CAN", "pass"], ["TPMS", "skip"]]) | {"total": 2, "passed": 1, "failed_components": [], "skipped": 1} | Checks the rule at a threshold. |
| 4 | inspect_components([]) | {"total": 0, "passed": 0, "failed_components": [], "skipped": 0} | Checks another valid input shape. |
| 5 | inspect_components([["A", "FAIL"], ["B", "PASS"], ["C", "FAIL"]]) | {"total": 3, "passed": 1, "failed_components": ["A", "C"], "skipped": 0} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of inspect_components that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, strings, loops, sets, functions, and validation.

### Rules and Constraints
- Use a for loop.
- Preserve duplicate component names.
- Do not sort or mutate input records.

### Hints
1. Normalize each result before branching.
2. Maintain independent counters.
3. Append failed names rather than using a set.

### Common Mistakes
- Dropping duplicate failures.
- Treating lowercase results as invalid.
- Counting SKIP as pass.

### Extension Challenge
Return the first failed component index, or None when all pass.
