# 09 - Diagnostic Retries - Medium

## Question Details
- Concept: while loops with bounded retries
- Supporting concepts: Lists, booleans, validation, early termination
- Difficulty: Medium
- Domain: Offline diagnostic retry simulation
- Learning Objective: Use a bounded while loop to retry simulated diagnostic responses safely.

## Scenario
A diagnostic tool may retry a request when a simulated response is TIMEOUT. A successful response is OK; any other response is a failure.

## Function Details
- Function signature: `run_diagnostic_retries(responses: list[str], max_attempts: int) -> tuple[str, int]`
- Behavior / return shape: Return the response outcome and number of attempts used.
- Exact accepted inputs: Responses contain 1 to 100 labels, each `OK`, `TIMEOUT`, or `ERROR`, case-insensitive. `max_attempts` is 1 through 100 and cannot exceed the response count. Reject invalid input with `ValueError`.
- Output and validation / behavior: Return `("SUCCESS", attempts)` at the first `OK`; return `("FAILED", attempts)` after the first non-timeout failure or after the retry limit. Attempts count inspected responses.

## Tasks to Implement
1. Implement `run_diagnostic_retries` with the exact signature above and validate the inputs against these accepted rules: Responses contain 1 to 100 labels, each `OK`, `TIMEOUT`, or `ERROR`, case-insensitive. `max_attempts` is 1 through 100 and cannot exceed the response count. Reject invalid input with `ValueError`.
2. Return the response outcome and number of attempts used.
3. Implement this output contract exactly: Return `("SUCCESS", attempts)` at the first `OK`; return `("FAILED", attempts)` after the first non-timeout failure or after the retry limit. Attempts count inspected responses.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | run_diagnostic_retries(["OK"], 1) | ("SUCCESS", 1) | Typical valid input. |
| 2 | run_diagnostic_retries(["TIMEOUT", "OK"], 2) | ("SUCCESS", 2) | Valid boundary case. |
| 3 | run_diagnostic_retries(["ERROR", "OK"], 2) | ("FAILED", 1) | Checks the rule at a threshold. |
| 4 | run_diagnostic_retries(["TIMEOUT", "ERROR", "OK"], 3) | ("FAILED", 2) | Checks another valid input shape. |
| 5 | run_diagnostic_retries(["TIMEOUT", "TIMEOUT", "OK"], 2) | ("FAILED", 2) | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of run_diagnostic_retries that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, loops, booleans, functions, and exceptions.

### Rules and Constraints
- Use a while loop.
- Stop as soon as success or permanent failure occurs.
- Do not retry ERROR.

### Hints
1. Track both index and attempts.
2. Stop on OK or ERROR.
3. The loop condition should include the retry limit.

### Common Mistakes
- Retrying after ERROR.
- Reading past the response list.
- Ignoring max_attempts.

### Extension Challenge
Return the normalized response history that was actually inspected.
