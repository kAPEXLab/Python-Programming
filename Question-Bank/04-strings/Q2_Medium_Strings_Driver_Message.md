# 04 - Driver Message - Medium

## Question Details
- Concept: Strings and string formatting
- Supporting concepts: Lists, validation, conditionals, numeric formatting
- Difficulty: Medium
- Domain: Driver information display
- Learning Objective: Construct a consistent human-readable message from validated vehicle status fields.

## Scenario
A simulated vehicle display shows a driver message based on speed, outside temperature, and warning labels. It must be concise and deterministic.

## Function Details
- Function signature: `build_driver_message(speed_kmh: float, temperature_c: float, warnings: list[str]) -> str`
- Behavior / return shape: Build a status message containing speed and temperature, followed by warnings in their supplied order.
- Exact accepted inputs: Speed: 0 through 300 km/h; Temperature: -50 through 60 degrees Celsius; Warnings: at most five non-empty strings, each at most 30 characters; Reject invalid inputs with `ValueError`.
- Output and validation / behavior: Return `Speed: X.X km/h | Temperature: Y.Y C | Warnings: A, B`. Use `None` when there are no warnings and one decimal place for measurements.

## Tasks to Implement
1. Implement `build_driver_message` with the exact signature above and validate the inputs against these accepted rules: Speed: 0 through 300 km/h; Temperature: -50 through 60 degrees Celsius; Warnings: at most five non-empty strings, each at most 30 characters; Reject invalid inputs with `ValueError`.
2. Build a status message containing speed and temperature, followed by warnings in their supplied order.
3. Implement this output contract exactly: Return `Speed: X.X km/h | Temperature: Y.Y C | Warnings: A, B`. Use `None` when there are no warnings and one decimal place for measurements.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | build_driver_message(0, -50, []) | Speed: 0.0 km/h | Temperature: -50.0 C | Warnings: None | Typical valid input. |
| 2 | build_driver_message(300, 60, ["LOW_BATTERY"]) | Speed: 300.0 km/h | Temperature: 60.0 C | Warnings: LOW_BATTERY | Valid lower or upper boundary. |
| 3 | build_driver_message(120.5, 20.25, ["ABS", "TPMS"]) | Speed: 120.5 km/h | Temperature: 20.3 C | Warnings: ABS, TPMS | Checks the threshold rule. |
| 4 | build_driver_message(50, 0, ["A", "A"]) | Speed: 50.0 km/h | Temperature: 0.0 C | Warnings: A, A | Checks a second valid shape or aggregate. |
| 5 | build_driver_message(299.9, -49.9, ["WARN1", "WARN2", "WARN3", "WARN4", "WARN5"]) | Speed: 299.9 km/h | Temperature: -49.9 C | Warnings: WARN1, WARN2, WARN3, WARN4, WARN5 | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of build_driver_message that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Strings, lists, functions, conditionals, and f-strings.

### Rules and Constraints
- Preserve warning order and spelling.
- Do not deduplicate warnings.
- Do not add a warning automatically.
- Do not mutate the warning list.

### Hints
1. Validate the whole warning list before joining it.
2. Use ", ".join(...) for multiple labels.
3. Use a separate display value for the empty-list case.

### Common Mistakes
- Sorting or deduplicating warnings.
- Formatting with too many decimal places.
- Printing [] instead of None.

### Extension Challenge
Wrap the message to a maximum of 40 characters per display line and return a list of lines.
