# 06 - Battery Health - Medium

## Question Details
- Concept: if-else and if-elif-else statements
- Supporting concepts: Numeric ranges, validation, formatted messages
- Difficulty: Medium
- Domain: Electric-vehicle battery health
- Learning Objective: Use ordered conditional branches to classify battery state of charge (SOC), the percentage of usable energy remaining.

## Scenario
Battery SOC is expressed as a percentage from 0% to 100%. A simulated dashboard labels SOC below 20% as LOW, 20% through 80% as OK, and above 80% as HIGH.

## Function Details
- Function signature: `classify_battery_soc(soc_percent: float) -> str`
- Behavior / return shape: Return a message containing the SOC and its classification.
- Exact accepted inputs: SOC must be from 0 through 100 percent inclusive. Reject other values with `ValueError`.
- Output and validation / behavior: Return `SOC: X.0% - STATUS`, displaying one decimal place; classify SOC below 20% as `LOW`, 20% through 80% as `OK`, and above 80% as `HIGH`.

## Tasks to Implement
1. Implement `classify_battery_soc` with the exact signature above and validate the inputs against these accepted rules: SOC must be from 0 through 100 percent inclusive. Reject other values with `ValueError`.
2. Return a message containing the SOC and its classification.
3. Implement this output contract exactly: Return `SOC: X.0% - STATUS`, displaying one decimal place; classify SOC below 20% as `LOW`, 20% through 80% as `OK`, and above 80% as `HIGH`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | classify_battery_soc(0) | SOC: 0.0% - LOW | Typical valid input. |
| 2 | classify_battery_soc(19.9) | SOC: 19.9% - LOW | Valid lower or upper boundary. |
| 3 | classify_battery_soc(20) | SOC: 20.0% - OK | Checks the threshold rule. |
| 4 | classify_battery_soc(80) | SOC: 80.0% - OK | Checks a second valid shape or aggregate. |
| 5 | classify_battery_soc(100) | SOC: 100.0% - HIGH | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of classify_battery_soc that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Functions, numeric comparisons, ranges, and formatted strings.

### Rules and Constraints
- Use if-elif-else.
- Use boundaries exactly as stated.
- Do not round before classification.

### Hints
1. Validate first.
2. Test the lowest interval before the middle interval.
3. Format only the displayed percentage.

### Common Mistakes
- Classifying 20% as low.
- Classifying 80% as high.
- Rounding before comparing.

### Extension Challenge
Add a CRITICAL state for SOC below 5%.
