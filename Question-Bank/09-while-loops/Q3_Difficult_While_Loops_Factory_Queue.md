# 09 - Factory Queue - Difficult

## Question Details
- Concept: while loops for stateful processing
- Supporting concepts: Lists, dictionaries, validation, queue simulation
- Difficulty: Difficult
- Domain: Manufacturing work queue
- Learning Objective: Process a simulated factory queue until empty while maintaining state and a complete result summary.

## Scenario
A factory station processes jobs in first-in-first-out order. Each job has an ID, processing time in minutes, and result PASS or FAIL.

## Function Details
- Function signature: `process_factory_queue(jobs: list[dict[str, object]]) -> dict[str, object]`
- Behavior / return shape: Process every job and report completion order, total time, and failed job IDs.
- Exact accepted inputs: 0 to 10,000 jobs; Each job has unique non-empty `job_id`, `minutes` from 0 through 480, and result `PASS` or `FAIL`; Reject duplicates, missing fields, or malformed values with `ValueError`.
- Output and validation / behavior: Return `completed_ids` in queue order, `total_minutes` as a number, and `failed_ids` in queue order. Zero jobs return empty lists and zero minutes.

## Tasks to Implement
1. Implement `process_factory_queue` with the exact signature above and validate the inputs against these accepted rules: 0 to 10,000 jobs; Each job has unique non-empty `job_id`, `minutes` from 0 through 480, and result `PASS` or `FAIL`; Reject duplicates, missing fields, or malformed values with `ValueError`.
2. Process every job and report completion order, total time, and failed job IDs.
3. Implement this output contract exactly: Return `completed_ids` in queue order, `total_minutes` as a number, and `failed_ids` in queue order. Zero jobs return empty lists and zero minutes.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | process_factory_queue([{"job_id": "J1", "minutes": 10, "result": "PASS"}]) | {"completed_ids": ["J1"], "total_minutes": 10, "failed_ids": []} | Typical valid input. |
| 2 | process_factory_queue([{"job_id": "J1", "minutes": 0, "result": "FAIL"}, {"job_id": "J2", "minutes": 480, "result": "PASS"}]) | {"completed_ids": ["J1", "J2"], "total_minutes": 480, "failed_ids": ["J1"]} | Valid boundary case. |
| 3 | process_factory_queue([{"job_id": "A", "minutes": 15, "result": "FAIL"}, {"job_id": "B", "minutes": 20, "result": "FAIL"}]) | {"completed_ids": ["A", "B"], "total_minutes": 35, "failed_ids": ["A", "B"]} | Checks the rule at a threshold. |
| 4 | process_factory_queue([]) | {"completed_ids": [], "total_minutes": 0, "failed_ids": []} | Checks another valid input shape. |
| 5 | process_factory_queue([{"job_id": "LAST", "minutes": 480, "result": "PASS"}]) | {"completed_ids": ["LAST"], "total_minutes": 480, "failed_ids": []} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of process_factory_queue that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, dictionaries, loops, conditionals, functions, and validation.

### Rules and Constraints
- Use a while loop that removes or advances through the queue.
- Do not reorder jobs.
- Do not mutate the caller's list.
- Validate all jobs before processing.

### Hints
1. Validate IDs with a set before processing.
2. Use an index or a shallow copy to protect the input list.
3. Advance exactly once per completed job.

### Common Mistakes
- Processing jobs out of order.
- Mutating the caller's list with pop().
- Counting failed time differently from passed time.

### Extension Challenge
Support a priority field while still processing FIFO within equal priorities.
