# 10 - Test Stubs - Difficult

## Question Details
- Concept: pass, continue, and break
- Supporting concepts: Test case processing, validation, reporting, dictionaries
- Difficulty: Difficult
- Domain: Offline automotive test runner
- Learning Objective: Use all three loop-control statements deliberately while building a deterministic test-run summary.

## Scenario
An offline test runner receives test cases. TODO cases are placeholders, invalid cases are skipped, and STOP ends the run. Valid cases have a boolean passed field.

## Function Details
- Function signature: `run_test_plan(cases: list[dict[str, object]]) -> dict[str, object]`
- Behavior / return shape: Summarize executed, skipped, placeholder, and failed test cases before the stop marker.
- Exact accepted inputs: Each case has `id` and `kind`. Kinds are `TEST`, `TODO`, `STOP`, or anything invalid. `TEST` requires boolean `passed`; IDs must be non-empty strings. Invalid cases are skipped. Input length is 0 to 10,000.
- Output and validation / behavior: `executed` counts valid `TEST` cases, `passed` counts passing tests, `failed_ids` preserves order, `skipped` counts invalid cases, and `placeholders` counts `TODO`. `STOP` is not counted and ends processing.

## Tasks to Implement
1. Implement `run_test_plan` with the exact signature above and validate the inputs against these accepted rules: Each case has `id` and `kind`. Kinds are `TEST`, `TODO`, `STOP`, or anything invalid. `TEST` requires boolean `passed`; IDs must be non-empty strings. Invalid cases are skipped. Input length is 0 to 10,000.
2. Summarize executed, skipped, placeholder, and failed test cases before the stop marker.
3. Return exactly the specified result: `executed` counts valid `TEST` cases, `passed` counts passing tests, `failed_ids` preserves order, `skipped` counts invalid cases, and `placeholders` counts `TODO`. `STOP` is not counted and ends processing.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | run_test_plan([{"id": "t1", "kind": "TEST", "passed": True}]) | {"executed": 1, "passed": 1, "failed_ids": [], "skipped": 0, "placeholders": 0} | Typical valid input. |
| 2 | run_test_plan([{"id": "t1", "kind": "TEST", "passed": False}, {"id": "t2", "kind": "TEST", "passed": True}]) | {"executed": 2, "passed": 1, "failed_ids": ["t1"], "skipped": 0, "placeholders": 0} | Valid boundary case. |
| 3 | run_test_plan([{"id": "todo", "kind": "TODO"}, {"id": "t", "kind": "TEST", "passed": True}]) | {"executed": 1, "passed": 1, "failed_ids": [], "skipped": 0, "placeholders": 1} | Checks the threshold rule. |
| 4 | run_test_plan([{"id": "bad", "kind": "OTHER"}, {"id": "stop", "kind": "STOP"}, {"id": "later", "kind": "TODO"}]) | {"executed": 0, "passed": 0, "failed_ids": [], "skipped": 1, "placeholders": 0} | Checks an alternate valid shape. |
| 5 | run_test_plan([]) | {"executed": 0, "passed": 0, "failed_ids": [], "skipped": 0, "placeholders": 0} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of run_test_plan that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Loops, dictionaries, functions, conditionals, validation, and formatted results.

### Rules and Constraints
- Use pass in the TODO branch, continue for invalid cases, and break for STOP.
- A boolean is required for passed; do not accept integers as substitutes.
- Do not mutate input.

### Hints
1. Handle STOP before ordinary validation.
2. Keep a separate branch for placeholders.
3. Invalid cases should increment one counter and continue.

### Common Mistakes
- Counting TODO as executed.
- Processing cases after STOP.
- Treating 1 as the boolean True.

### Extension Challenge
Return the ID of the last executed test, or None when no test ran.
