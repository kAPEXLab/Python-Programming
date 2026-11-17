# 01 - Test Harness Layout - Difficult

## Question Details
- Concept: Python syntax and program structure
- Supporting concepts: Functions, nested data, validation, exceptions, modular decomposition
- Difficulty: Difficult
- Domain: Offline automotive test automation
- Learning Objective: Design a readable, multi-function Python program that validates and summarizes simulated test results.

## Scenario
A test harness runs offline checks against simulated vehicle components. Each result contains a component name, test name, status, and duration in seconds.

## Function Details
- Function signature: `summarize_test_batch(results: list[dict[str, object]]) -> str`
- Behavior / return shape: Create a summary for a batch of test results, including totals, pass rate, failed test names, and total execution time.
- Exact accepted inputs: `results`: 0 to 50,000 dictionaries; `component` and `test`: non-empty strings; `status`: exactly `PASS` or `FAIL`; `duration`: number from 0 through 3,600 seconds; Reject missing keys, wrong types, blank names, invalid statuses, or invalid durations with `ValueError`.
- Output and validation / behavior: Return: `Total tests: N\nPassed: P\nPass rate: X.XX%\nFailed tests: name1, name2\nTotal duration: Y.YY s` Use `None` on the failed-tests line when no test failed. Preserve input order for failed tests.

## Tasks to Implement
1. Implement `summarize_test_batch` with the exact signature above and validate the inputs against these accepted rules: `results`: 0 to 50,000 dictionaries; `component` and `test`: non-empty strings; `status`: exactly `PASS` or `FAIL`; `duration`: number from 0 through 3,600 seconds; Reject missing keys, wrong types, blank names, invalid statuses, or invalid durations with `ValueError`.
2. Create a summary for a batch of test results, including totals, pass rate, failed test names, and total execution time.
3. Return exactly the specified result: Return: `Total tests: N\nPassed: P\nPass rate: X.XX%\nFailed tests: name1, name2\nTotal duration: Y.YY s` Use `None` on the failed-tests line when no test failed. Preserve input order for failed tests.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | summarize_test_batch([{"component": "ECU", "test": "boot", "status": "PASS", "duration": 1.25}]) | Total tests: 1<br>Passed: 1<br>Pass rate: 100.00%<br>Failed tests: None<br>Total duration: 1.25 s | Typical valid input. |
| 2 | summarize_test_batch([{"component": "ABS", "test": "brake", "status": "FAIL", "duration": 2}, {"component": "ABS", "test": "sensor", "status": "PASS", "duration": 1}]) | Total tests: 2<br>Passed: 1<br>Pass rate: 50.00%<br>Failed tests: brake<br>Total duration: 3.00 s | Valid boundary or threshold case. |
| 3 | summarize_test_batch([{"component": "BMS", "test": "voltage", "status": "PASS", "duration": 0}]) | Total tests: 1<br>Passed: 1<br>Pass rate: 100.00%<br>Failed tests: None<br>Total duration: 0.00 s | Checks an alternate accepted value or input shape. |
| 4 | summarize_test_batch([]) | Total tests: 0<br>Passed: 0<br>Pass rate: 0.00%<br>Failed tests: None<br>Total duration: 0.00 s | Checks a second valid boundary or aggregation case. |
| 5 | summarize_test_batch([{"component": "CAN", "test": "timeout", "status": "FAIL", "duration": 3600}]) | Total tests: 1<br>Passed: 0<br>Pass rate: 0.00%<br>Failed tests: timeout<br>Total duration: 3600.00 s | Checks another valid input without changing the contract. |

## Expected Deliverables
- Complete implementation of summarize_test_batch that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Functions, collections, loops, conditionals, exceptions, and formatted strings.

### Rules and Constraints
- Use Python 3.12 or later.
- Use at least two helper functions in addition to the public function.
- Do not mutate input records.
- Pass rate is passed / total * 100; for zero tests use 0.00%.
- Raise ValueError for invalid data before returning a partial report.
- Display rates and duration to exactly two decimal places.

### Hints
- Correctness: 3 points
- Appropriate syntax and decomposition: 1 point
- Input validation: 1 point
- Edge-case handling: 1 point
- Readability and naming: 1 point
- Modularity: 1 point
- Efficiency: 0.5 point
- Documentation: 0.5 point
- Testability: 1 point
1. Validate a record in a dedicated helper before aggregating it.
2. Maintain separate counters and a list of failed test names.
3. Handle the zero-test pass-rate case explicitly.

### Common Mistakes
- Returning a partial result after encountering invalid data.
- Using dictionary keys without checking they exist.
- Losing failed-test order by converting names to a set.
- Formatting 50% instead of 50.00%.

### Extension Challenge
Add a per-component summary while keeping the five required lines unchanged.
