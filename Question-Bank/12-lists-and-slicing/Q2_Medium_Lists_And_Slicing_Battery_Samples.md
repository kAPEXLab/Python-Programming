# 12 - Battery Samples - Medium

## Question Details
- Concept: List slicing with a step
- Supporting concepts: Validation, aggregation, rounding, functions
- Difficulty: Medium
- Domain: Offline battery voltage sampling
- Learning Objective: Use slices with start, stop, and step values to separate alternating battery samples.

## Scenario
A battery test bench is recording voltage readings from a charging cycle while two sensor groups alternate in sequence. The first, third, fifth, and later readings belong to Channel A, while the second, fourth, and later readings belong to Channel B. Your task is to summarize the average voltage for each channel and confirm the total number of samples captured before the report is logged.

## Function Details
- Function signature: `summarize_battery_samples(samples: list[float]) -> dict[str, object]`
- Behavior / return shape: Summarize the average voltage of both alternating channels and the complete sample count.
- Exact accepted inputs: Provide 2 through 200 finite voltage readings from 10.0 through 16.0 volts. Values are measured to at most three decimals.
- Output and validation / behavior: Use `samples[::2]` for channel A and `samples[1::2]` for channel B. Return `channel_a_average`, `channel_b_average`, and `sample_count`, with averages rounded to two decimals.

## Tasks to Implement
1. Implement `summarize_battery_samples` with the exact signature above and validate the inputs against these accepted rules: Provide 2 through 200 finite voltage readings from 10.0 through 16.0 volts. Values are measured to at most three decimals.
2. Summarize the average voltage of both alternating channels and the complete sample count.
3. Return exactly the specified result: Use `samples[::2]` for channel A and `samples[1::2]` for channel B. Return `channel_a_average`, `channel_b_average`, and `sample_count`, with averages rounded to two decimals.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | summarize_battery_samples([10, 12]) | {"channel_a_average": 10.0, "channel_b_average": 12.0, "sample_count": 2} | Typical valid input. |
| 2 | summarize_battery_samples([12, 14, 10]) | {"channel_a_average": 11.0, "channel_b_average": 14.0, "sample_count": 3} | Valid boundary case. |
| 3 | summarize_battery_samples([10, 11, 12, 13]) | {"channel_a_average": 11.0, "channel_b_average": 12.0, "sample_count": 4} | Checks the threshold rule. |
| 4 | summarize_battery_samples([16, 15, 14, 13, 12]) | {"channel_a_average": 14.0, "channel_b_average": 14.0, "sample_count": 5} | Checks an alternate valid shape. |
| 5 | summarize_battery_samples([12.345, 12.346]) | {"channel_a_average": 12.35, "channel_b_average": 12.35, "sample_count": 2} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of summarize_battery_samples that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, slicing, arithmetic, dictionaries, functions, and exceptions.

### Rules and Constraints
- Preserve input order and do not mutate input.
- Channel B may contain one fewer sample.
- Raise ValueError for invalid values or fewer than two samples.
- Use slicing to form both channels.

### Hints
1. Validate with math.isfinite() before averaging.
2. Build each channel with a slice step of two.
3. Apply round(value, 2) only to the final averages.

### Common Mistakes
- Taking contiguous halves instead of alternating samples.
- Rounding each input before averaging.
- Dividing by the total sample count.

### Extension Challenge
Return the channel with the larger average, or "equal" when the rounded averages match.
