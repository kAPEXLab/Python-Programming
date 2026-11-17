# 03 - Battery Voltage - Medium

## Question Details
- Concept: Numeric data types and type conversion
- Supporting concepts: Lists, booleans, validation, rounding
- Difficulty: Medium
- Domain: Electric-vehicle battery voltage
- Learning Objective: Convert a sequence of voltage samples and classify the battery state from numeric values.

## Scenario
An electric vehicle battery pack is represented by simulated voltage samples in volts. A healthy sample lies from 300 through 420 V inclusive.

## Function Details
- Function signature: `analyze_battery_voltage(samples: list[float | int]) -> dict[str, object]`
- Behavior / return shape: Convert each voltage to millivolts, calculate the average, and set `all_healthy` true only when every sample is from 300 through 420 V inclusive.
- Exact accepted inputs: One to 1,000 samples; Every sample is numeric and from 0 through 500 V; Reject an empty list, nonnumeric values, or out-of-range values with `ValueError`.
- Output and validation / behavior: Return `{"millivolts": list[int], "average_volts": float, "all_healthy": bool}`. Millivolts are volts times 1,000. Average is rounded to two decimals.

## Tasks to Implement
1. Implement `analyze_battery_voltage` with the exact signature above and validate the inputs against these accepted rules: One to 1,000 samples; Every sample is numeric and from 0 through 500 V; Reject an empty list, nonnumeric values, or out-of-range values with `ValueError`.
2. Analyze samples and report converted millivolt values, the average voltage, and whether every sample is healthy.
3. Implement this output contract exactly: Return `{"millivolts": list[int], "average_volts": float, "all_healthy": bool}`. Millivolts are volts times 1,000. Average is rounded to two decimals.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | analyze_battery_voltage([300]) | {"millivolts": [300000], "average_volts": 300.0, "all_healthy": True} | Typical valid input. |
| 2 | analyze_battery_voltage([300, 420]) | {"millivolts": [300000, 420000], "average_volts": 360.0, "all_healthy": True} | Valid lower or upper boundary. |
| 3 | analyze_battery_voltage([0, 500]) | {"millivolts": [0, 500000], "average_volts": 250.0, "all_healthy": False} | Checks the threshold rule. |
| 4 | analyze_battery_voltage([350, 360, 370]) | {"millivolts": [350000, 360000, 370000], "average_volts": 360.0, "all_healthy": True} | Checks a second valid shape or aggregate. |
| 5 | analyze_battery_voltage([12.5, 12.5]) | {"millivolts": [12500, 12500], "average_volts": 12.5, "all_healthy": False} | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of analyze_battery_voltage that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, loops, numeric conversion, comparisons, and functions.

### Rules and Constraints
- Preserve sample order.
- Do not round converted millivolts.
- Healthy means every sample is in the inclusive 300-420 V interval.
- Do not mutate the input list.

### Hints
1. Convert each value independently while preserving order.
2. Use the original volt values for the average.
3. all() can express the health rule clearly.

### Common Mistakes
- Rounding millivolts to a float.
- Returning healthy when only some samples are healthy.
- Accepting an empty list.

### Extension Challenge
Return the indices of all unhealthy samples.
