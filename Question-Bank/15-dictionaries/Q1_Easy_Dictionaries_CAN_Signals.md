# 15 - CAN Signals - Easy

## Question Details
- Concept: Dictionary keys and values
- Supporting concepts: Lookup, validation, strings, functions
- Difficulty: Easy
- Domain: Simulated CAN signal registry
- Learning Objective: Use dictionary lookups to retrieve named signal values safely.

## Scenario
An offline data fixture maps signal names to their current numeric readings.

## Function Details
- Function signature: `read_can_signal(signals: dict[str, float], name: str) -> float | None`
- Behavior / return shape: Return the requested signal value and a clear missing-signal result.
- Exact accepted inputs: Signal names are non-empty strings. Values are finite numbers from -1000.0 through 1000.0. The requested name may include surrounding whitespace and is case-insensitive.
- Output and validation / behavior: Return the matching numeric value or `None` when no normalized key exists.

## Tasks to Implement
1. Implement `read_can_signal` with the exact signature above and validate the inputs against these accepted rules: Signal names are non-empty strings. Values are finite numbers from -1000.0 through 1000.0. The requested name may include surrounding whitespace and is case-insensitive.
2. Return the requested signal value and a clear missing-signal result.
3. Implement this output contract exactly: Return the matching numeric value or `None` when no normalized key exists.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | read_can_signal({"EngineSpeed": 1200}, " enginespeed ") | 1200 | Typical valid input. |
| 2 | read_can_signal({"BatteryVoltage": 400}, "batteryvoltage") | 400 | Valid boundary case. |
| 3 | read_can_signal({}, "missing") | None | Checks the threshold rule. |
| 4 | read_can_signal({"A": -1000}, "a") | -1000 | Checks an alternate valid shape. |
| 5 | read_can_signal({"speed": 300.5}, "SPEED") | 300.5 | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of read_can_signal that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Dictionaries, strings, numbers, functions, and conditionals.

### Rules and Constraints
- Normalize only the requested name and compare signal names case-insensitively.
- Reject malformed dictionaries or names with ValueError.
- Do not mutate input.

### Hints
1. Validate all dictionary entries first.
2. Strip and uppercase the requested name.
3. Search normalized keys without changing the source dictionary.

### Common Mistakes
- Raising KeyError for a missing signal.
- Mutating keys during normalization.
- Treating zero as missing.

### Extension Challenge
Return both the value and the normalized key as a tuple.
