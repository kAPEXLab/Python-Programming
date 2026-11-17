# 05 - Battery Power Calculation - Difficult

## Question Details
- Concept: Operator precedence and expressions
- Supporting concepts: Unit conversion, aggregation, validation, rounding
- Difficulty: Difficult
- Domain: Electric-vehicle battery power analysis
- Learning Objective: Construct unambiguous expressions and calculate electrical power and energy from sampled voltage and current.

## Scenario
A simulated battery log contains voltage in volts, current in amperes, and sample duration in seconds. Instantaneous power is voltage * current; energy is power times time, converted from joules to watt-hours by dividing by 3,600.

## Function Details
- Function signature: `analyze_power_samples(samples: list[tuple[float, float, float]]) -> dict[str, float]`
- Behavior / return shape: Calculate total energy and peak power for a sequence of samples.
- Exact accepted inputs: One to 10,000 samples; Voltage: 0 through 1,000 V; Current: -500 through 500 A; negative means charging; Duration: 0.01 through 3,600 seconds; Reject malformed samples or invalid values with `ValueError`.
- Output and validation / behavior: Return `total_energy_wh` as the sum of each `voltage * current * duration / 3600`, and `peak_power_w` as the largest absolute `voltage * current`; round both fields to two decimals.

## Tasks to Implement
1. Implement `analyze_power_samples` with the exact signature above and validate the inputs against these accepted rules: One to 10,000 samples; Voltage: 0 through 1,000 V; Current: -500 through 500 A; negative means charging; Duration: 0.01 through 3,600 seconds; Reject malformed samples or invalid values with `ValueError`.
2. Calculate total energy and peak power for a sequence of samples.
3. Implement this output contract exactly: Return `total_energy_wh` as the sum of each `voltage * current * duration / 3600`, and `peak_power_w` as the largest absolute `voltage * current`; round both fields to two decimals.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | analyze_power_samples([(400, 10, 3600)]) | {"total_energy_wh": 4000.0, "peak_power_w": 4000.0} | Typical valid input. |
| 2 | analyze_power_samples([(400, -10, 3600)]) | {"total_energy_wh": -4000.0, "peak_power_w": 4000.0} | Valid lower or upper boundary. |
| 3 | analyze_power_samples([(0, 500, 0.01)]) | {"total_energy_wh": 0.0, "peak_power_w": 0.0} | Checks the threshold rule. |
| 4 | analyze_power_samples([(100, 10, 1800), (200, 5, 3600)]) | {"total_energy_wh": 1500.0, "peak_power_w": 1000.0} | Checks a second valid shape or aggregate. |
| 5 | analyze_power_samples([(1000, 500, 3600)]) | {"total_energy_wh": 500000.0, "peak_power_w": 500000.0} | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of analyze_power_samples that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, loops, arithmetic, boolean validation, and functions.

### Rules and Constraints
- Parenthesize expressions where conversion order matters.
- Peak power is the largest absolute power, reported as a nonnegative value.
- Do not round intermediate products.
- Preserve no mutable global state.

### Hints
1. Calculate one sample's power before calculating its energy.
2. Divide joules by 3,600 only after multiplying power by seconds.
3. Use absolute power only for the peak comparison.

### Common Mistakes
- Dividing voltage or current by 3,600.
- Losing the negative sign for charging energy.
- Using signed power to calculate peak magnitude.

### Extension Challenge
Return separate positive discharge energy and negative charging energy totals.
