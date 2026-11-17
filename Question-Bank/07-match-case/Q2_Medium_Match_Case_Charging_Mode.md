# 07 - Charging Mode - Medium

## Question Details
- Concept: match-case with guarded patterns
- Supporting concepts: Dictionaries, validation, numeric comparisons
- Difficulty: Medium
- Domain: Electric-vehicle charging
- Learning Objective: Use pattern matching and guards to classify a charging request.

## Scenario
A charging station receives a simulated request containing connector type and requested current. AC charging supports up to 32 A; DC fast charging supports up to 200 A.

## Function Details
- Function signature: `evaluate_charging_request(request: dict[str, object]) -> str`
- Behavior / return shape: Return the charging mode and whether the request is accepted.
- Exact accepted inputs: The request dictionary requires `connector` and `current_a`; current must be 0 through 200 A. AC current must be at most 32 A, DC current may be 0 through 200 A. A non-empty connector other than `AC` or `DC` returns `UNKNOWN_CONNECTOR`; missing, blank, non-string, or otherwise malformed required fields raise `ValueError`.
- Output and validation / behavior: Return `AC_ACCEPTED`, `DC_ACCEPTED`, `AC_CURRENT_TOO_HIGH`, `DC_CURRENT_TOO_HIGH`, or `UNKNOWN_CONNECTOR`.

## Tasks to Implement
1. Implement `evaluate_charging_request` with the exact signature above and validate the inputs against these accepted rules: The request dictionary requires `connector` and `current_a`; current must be 0 through 200 A. AC current must be at most 32 A, DC current may be 0 through 200 A. A non-empty connector other than `AC` or `DC` returns `UNKNOWN_CONNECTOR`; missing, blank, non-string, or otherwise malformed required fields raise `ValueError`.
2. Return the charging mode and whether the request is accepted.
3. Implement this output contract exactly: Return `AC_ACCEPTED`, `DC_ACCEPTED`, `AC_CURRENT_TOO_HIGH`, `DC_CURRENT_TOO_HIGH`, or `UNKNOWN_CONNECTOR`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | evaluate_charging_request({"connector": "AC", "current_a": 32}) | AC_ACCEPTED | Typical valid input. |
| 2 | evaluate_charging_request({"connector": "AC", "current_a": 32.1}) | AC_CURRENT_TOO_HIGH | Valid lower or upper boundary. |
| 3 | evaluate_charging_request({"connector": "DC", "current_a": 200}) | DC_ACCEPTED | Checks the threshold rule. |
| 4 | evaluate_charging_request({"connector": "DC", "current_a": 50}) | DC_ACCEPTED | Checks a second valid shape or aggregate. |
| 5 | evaluate_charging_request({"connector": "XYZ", "current_a": 10}) | UNKNOWN_CONNECTOR | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of evaluate_charging_request that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
match-case, functions, dictionaries, comparisons, and exceptions.

### Rules and Constraints
- Use match-case on the connector.
- Treat connector matching as case-insensitive.
- Unknown non-empty connector values are not malformed and return UNKNOWN_CONNECTOR.
- Current exactly at the limit is accepted.

### Hints
1. Validate the dictionary shape before matching.
2. Normalize the connector value.
3. Use a guard to compare current against 32 A.

### Common Mistakes
- Applying the AC limit to DC.
- Accepting missing fields as zero.
- Making the limit exclusive.

### Extension Challenge
Support a THREE_PHASE_AC connector with a 63 A limit.
