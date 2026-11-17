# 07 - Diagnostic Status - Easy

## Question Details
- Concept: match-case statements
- Supporting concepts: Strings, validation, return values
- Difficulty: Easy
- Domain: Vehicle diagnostics
- Learning Objective: Use structural pattern matching to map discrete diagnostic codes to status labels.

## Scenario
A diagnostic trouble code (DTC) is a short code representing a detected issue. This offline exercise uses four simulated codes.

## Function Details
- Function signature: `diagnostic_status(code: str) -> str`
- Behavior / return shape: Translate a DTC into a dashboard status.
- Exact accepted inputs: `code` must be a non-empty string. Matching is case-insensitive after trimming whitespace. Unknown codes are valid inputs.
- Output and validation / behavior: Map `P0000` to `CLEAR`, `P0300` to `ENGINE_MISFIRE`, `B0001` to `BODY_SENSOR_FAULT`, and `U0100` to `COMMUNICATION_FAULT`; return `UNKNOWN_CODE` for any other non-empty normalized code.

## Tasks to Implement
1. Implement `diagnostic_status` with the exact signature above and validate the inputs against these accepted rules: `code` must be a non-empty string. Matching is case-insensitive after trimming whitespace. Unknown codes are valid inputs.
2. Translate a DTC into a dashboard status.
3. Implement this output contract exactly: Map `P0000` to `CLEAR`, `P0300` to `ENGINE_MISFIRE`, `B0001` to `BODY_SENSOR_FAULT`, and `U0100` to `COMMUNICATION_FAULT`; return `UNKNOWN_CODE` for any other non-empty normalized code.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | diagnostic_status("P0000") | CLEAR | Typical valid input. |
| 2 | diagnostic_status("p0300") | ENGINE_MISFIRE | Valid lower or upper boundary. |
| 3 | diagnostic_status(" B0001 ") | BODY_SENSOR_FAULT | Checks the threshold rule. |
| 4 | diagnostic_status("U0100") | COMMUNICATION_FAULT | Checks a second valid shape or aggregate. |
| 5 | diagnostic_status("P9999") | UNKNOWN_CODE | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of diagnostic_status that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Functions, strings, conditionals, and basic validation.

### Rules and Constraints
- Use match-case, not a long if-elif chain.
- Normalize whitespace and case once.
- Raise ValueError for a blank code.

### Hints
1. Normalize the code before matching.
2. Add one case for each known code.
3. Use _ for unknown values.

### Common Mistakes
- Forgetting case normalization.
- Treating unknown codes as errors.
- Using pattern matching syntax incorrectly.

### Extension Challenge
Return a tuple containing the status and a severity label.
