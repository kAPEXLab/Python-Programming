# 07 - Gear Selector - Difficult

## Question Details
- Concept: Advanced structural pattern matching
- Supporting concepts: Nested dictionaries, guards, validation, domain rules
- Difficulty: Difficult
- Domain: Offline gear-selector simulation
- Learning Objective: Match nested state records and apply guarded rules without controlling real vehicle hardware.

## Scenario
A simulated gear selector reports the requested gear and vehicle speed. The exercise only creates a text decision; it must never connect to a real vehicle.

## Function Details
- Function signature: `evaluate_gear_request(state: dict[str, object]) -> str`
- Behavior / return shape: Decide whether a requested gear change is permitted under simplified offline rules.
- Exact accepted inputs: The state dictionary requires `requested_gear` and `speed_kmh`; speed is 0 through 300 km/h. `P` is allowed only at 0; `R` only from 0 through 5 inclusive; `N` is always allowed; `D` is allowed above 0. Unknown gears are invalid. Raise `ValueError` for malformed input.
- Output and validation / behavior: Return `ALLOWED_<gear>` or `REJECTED_<gear>`, such as `ALLOWED_R`.

## Tasks to Implement
1. Implement `evaluate_gear_request` with the exact signature above and validate the inputs against these accepted rules: The state dictionary requires `requested_gear` and `speed_kmh`; speed is 0 through 300 km/h. `P` is allowed only at 0; `R` only from 0 through 5 inclusive; `N` is always allowed; `D` is allowed above 0. Unknown gears are invalid. Raise `ValueError` for malformed input.
2. Decide whether a requested gear change is permitted under simplified offline rules.
3. Implement this output contract exactly: Return `ALLOWED_<gear>` or `REJECTED_<gear>`, such as `ALLOWED_R`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | evaluate_gear_request({"requested_gear": "P", "speed_kmh": 0}) | ALLOWED_P | Typical valid input. |
| 2 | evaluate_gear_request({"requested_gear": "R", "speed_kmh": 5}) | ALLOWED_R | Valid lower or upper boundary. |
| 3 | evaluate_gear_request({"requested_gear": "R", "speed_kmh": 6}) | REJECTED_R | Checks the threshold rule. |
| 4 | evaluate_gear_request({"requested_gear": "N", "speed_kmh": 100}) | ALLOWED_N | Checks a second valid shape or aggregate. |
| 5 | evaluate_gear_request({"requested_gear": "D", "speed_kmh": 0}) | REJECTED_D | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of evaluate_gear_request that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Dictionaries, functions, validation, match-case, and boolean logic.

### Rules and Constraints
- Use match-case with guards.
- Normalize gear strings.
- This is an offline simulation only.

### Hints
1. Extract and normalize the two fields first.
2. Match each gear separately.
3. Put the speed condition in a guard.

### Common Mistakes
- Allowing reverse at any speed.
- Treating missing fields as valid.
- Writing real actuator commands instead of returning a simulation result.

### Extension Challenge
Add a vehicle_mode field where TOW permits only N.
