# 15 - Vehicle Configuration - Medium

## Question Details
- Concept: Dictionary updates and defaults
- Supporting concepts: Nested dictionaries, validation, copying, functions
- Difficulty: Medium
- Domain: Offline vehicle configuration profile
- Learning Objective: Read optional configuration fields and produce a validated configuration with defaults.

## Scenario
A simulation stores optional vehicle settings for drive mode, maximum speed, and regenerative braking.

## Function Details
- Function signature: `complete_vehicle_configuration(config: dict[str, object]) -> dict[str, object]`
- Behavior / return shape: Build a complete configuration record without changing the caller's dictionary.
- Exact accepted inputs: Allowed keys are `drive_mode`, `max_speed_kmh`, and `regen_enabled`. Defaults are `"NORMAL"`, `120`, and `True`. Mode is `NORMAL`, `ECO`, or `SPORT`; speed is an integer 40 through 240; regen is boolean.
- Output and validation / behavior: Return a new dictionary containing all three keys. Normalize mode to uppercase. Preserve no unknown keys.

## Tasks to Implement
1. Implement `complete_vehicle_configuration` with the exact signature above and validate the inputs against these accepted rules: Allowed keys are `drive_mode`, `max_speed_kmh`, and `regen_enabled`. Defaults are `"NORMAL"`, `120`, and `True`. Mode is `NORMAL`, `ECO`, or `SPORT`; speed is an integer 40 through 240; regen is boolean.
2. Build a complete configuration record without changing the caller's dictionary.
3. Implement this output contract exactly: Return a new dictionary containing all three keys. Normalize mode to uppercase. Preserve no unknown keys.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | complete_vehicle_configuration({}) | {"drive_mode": "NORMAL", "max_speed_kmh": 120, "regen_enabled": True} | Typical valid input. |
| 2 | complete_vehicle_configuration({"drive_mode": "eco"}) | {"drive_mode": "ECO", "max_speed_kmh": 120, "regen_enabled": True} | Valid boundary case. |
| 3 | complete_vehicle_configuration({"max_speed_kmh": 240}) | {"drive_mode": "NORMAL", "max_speed_kmh": 240, "regen_enabled": True} | Checks the threshold rule. |
| 4 | complete_vehicle_configuration({"regen_enabled": False}) | {"drive_mode": "NORMAL", "max_speed_kmh": 120, "regen_enabled": False} | Checks an alternate valid shape. |
| 5 | complete_vehicle_configuration({"drive_mode": "SPORT", "max_speed_kmh": 40, "regen_enabled": True}) | {"drive_mode": "SPORT", "max_speed_kmh": 40, "regen_enabled": True} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of complete_vehicle_configuration that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Dictionaries, strings, booleans, numbers, functions, and exceptions.

### Rules and Constraints
- Missing keys receive defaults.
- Reject unknown keys or invalid types and ranges with ValueError.
- Do not mutate input.

### Hints
1. Validate keys before reading values.
2. Use a fresh result dictionary.
3. Check booleans before general integer checks.

### Common Mistakes
- Modifying the input dictionary with setdefault.
- Accepting unknown options silently.
- Treating True as the integer 1.

### Extension Challenge
Add a fourth optional setting while retaining rejection of unknown keys.
