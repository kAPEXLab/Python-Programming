# 17 - Quality Batches - Difficult

## Question Details
- Concept: Multi-level collection traversal
- Supporting concepts: Nested dictionaries, validation, filtering, statistics
- Difficulty: Difficult
- Domain: Offline production quality batches
- Learning Objective: Analyze batches containing vehicles and component inspection results.

## Scenario
A factory fixture groups inspection results by batch, then vehicle, then component.

## Function Details
- Function signature: `quality_batch_report(batches: list[dict[str, object]], threshold: float = 0.95) -> dict[str, object]`
- Behavior / return shape: Calculate pass rates per batch and identify batches below a quality threshold.
- Exact accepted inputs: Each batch has unique non-empty `batch_id` and `vehicles`. Each vehicle has unique `vehicle_id` within its batch and `checks`, a list of `PASS` or `FAIL` strings. Threshold is finite from 0.0 through 1.0.
- Output and validation / behavior: Return `pass_rates` mapping batch IDs to rates rounded to three decimals and `below_threshold` as a set. A batch with zero checks has rate `None` and is below threshold.

## Tasks to Implement
1. Implement `quality_batch_report` with the exact signature above and validate the inputs against these accepted rules: Each batch has unique non-empty `batch_id` and `vehicles`. Each vehicle has unique `vehicle_id` within its batch and `checks`, a list of `PASS` or `FAIL` strings. Threshold is finite from 0.0 through 1.0.
2. Calculate pass rates per batch and identify batches below a quality threshold.
3. Implement this output contract exactly: Return `pass_rates` mapping batch IDs to rates rounded to three decimals and `below_threshold` as a set. A batch with zero checks has rate `None` and is below threshold.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | quality_batch_report([{"batch_id": "B1", "vehicles": [{"vehicle_id": "V1", "checks": ["PASS", "FAIL"]}]}], 0.5) | {"pass_rates": {"B1": 0.5}, "below_threshold": set()} | Typical valid input. |
| 2 | quality_batch_report([{"batch_id": "B1", "vehicles": [{"vehicle_id": "V1", "checks": ["PASS"]}]}], 1.0) | {"pass_rates": {"B1": 1.0}, "below_threshold": set()} | Confirms a batch exactly at the threshold is not below it. |
| 3 | quality_batch_report([{"batch_id": "B1", "vehicles": [{"vehicle_id": "V1", "checks": []}]}], 0.95) | {"pass_rates": {"B1": None}, "below_threshold": {"B1"}} | A vehicle with no checks has no measurable pass rate and is below threshold. |
| 4 | quality_batch_report([{"batch_id": "B1", "vehicles": [{"vehicle_id": "V1", "checks": ["PASS", "PASS", "FAIL"]}]}], 0.95) | {"pass_rates": {"B1": 0.667}, "below_threshold": {"B1"}} | Checks an aggregation boundary. |
| 5 | quality_batch_report([{"batch_id": "A", "vehicles": [{"vehicle_id": "V", "checks": ["PASS"]}]}, {"batch_id": "B", "vehicles": [{"vehicle_id": "V", "checks": ["FAIL"]}]}], 0.5) | {"pass_rates": {"A": 1.0, "B": 0.0}, "below_threshold": {"B"}} | Aggregates separate batches and applies the threshold independently. |

## Expected Deliverables
- Complete implementation of quality_batch_report that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Nested collections, loops, dictionaries, booleans, validation, and rounding.

### Rules and Constraints
- Count every check exactly once.
- Reject malformed data and duplicate IDs with ValueError.
- Do not mutate input.

### Hints
1. Keep pass and total counters per batch.
2. Handle zero total before division.
3. Compare the unrounded rate to the threshold, then report the rounded rate.

### Common Mistakes
- Comparing rounded rates to the threshold.
- Counting vehicles instead of checks.
- Treating an empty batch as perfect quality.

### Extension Challenge
Return the first failed component index for every vehicle in below-threshold batches.
