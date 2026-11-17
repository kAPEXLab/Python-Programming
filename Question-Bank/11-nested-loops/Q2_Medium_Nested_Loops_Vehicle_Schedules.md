# 11 - Vehicle Schedules - Medium

## Question Details
- Concept: Nested loops and pair comparison
- Supporting concepts: Dictionaries, lists, validation, conflict detection
- Difficulty: Medium
- Domain: Fleet service scheduling
- Learning Objective: Compare every pair of scheduled jobs to detect overlapping work for the same vehicle.

## Scenario
A fleet workshop schedules jobs using start and end times in minutes from the beginning of a day. Two jobs conflict if they target the same vehicle and their time intervals overlap.

## Function Details
- Function signature: `find_schedule_conflicts(jobs: list[dict[str, object]]) -> list[tuple[str, str]]`
- Behavior / return shape: Return the IDs of all conflicting job pairs in input order.
- Exact accepted inputs: Each job has a unique `job_id`, `vehicle_id`, `start_minute`, and `end_minute`; accept 0–2,000 jobs with integer times from 0 through 1,440 and `start_minute < end_minute`. Intervals are half-open, so a job ending at 100 does not conflict with one starting at 100.
- Output and validation / behavior: Return pairs `(earlier_input_job_id, later_input_job_id)` for conflicts, ordered by first index then second index.

## Tasks to Implement
1. Implement `find_schedule_conflicts` with the exact signature above and validate the inputs against these accepted rules: Each job has a unique `job_id`, `vehicle_id`, `start_minute`, and `end_minute`; accept 0–2,000 jobs with integer times from 0 through 1,440 and `start_minute < end_minute`. Intervals are half-open, so a job ending at 100 does not conflict with one starting at 100.
2. Return the IDs of all conflicting job pairs in input order.
3. Implement this output contract exactly: Return pairs `(earlier_input_job_id, later_input_job_id)` for conflicts, ordered by first index then second index.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | find_schedule_conflicts([{"job_id": "A", "vehicle_id": "V", "start_minute": 0, "end_minute": 100}, {"job_id": "B", "vehicle_id": "V", "start_minute": 99, "end_minute": 120}]) | [("A", "B")] | Typical valid input. |
| 2 | find_schedule_conflicts([{"job_id": "A", "vehicle_id": "V", "start_minute": 0, "end_minute": 100}, {"job_id": "B", "vehicle_id": "V", "start_minute": 100, "end_minute": 120}]) | [] | Valid boundary case. |
| 3 | find_schedule_conflicts([{"job_id": "A", "vehicle_id": "V1", "start_minute": 0, "end_minute": 10}, {"job_id": "B", "vehicle_id": "V2", "start_minute": 5, "end_minute": 15}]) | [] | Checks the threshold rule. |
| 4 | find_schedule_conflicts([{"job_id": "A", "vehicle_id": "V", "start_minute": 0, "end_minute": 20}, {"job_id": "B", "vehicle_id": "V", "start_minute": 5, "end_minute": 10}, {"job_id": "C", "vehicle_id": "V", "start_minute": 19, "end_minute": 30}]) | [("A", "B"), ("A", "C")] | Checks an alternate valid shape. |
| 5 | find_schedule_conflicts([]) | [] | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of find_schedule_conflicts that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Nested loops, dictionaries, tuples, conditionals, and validation.

### Rules and Constraints
- Use nested loops to compare pairs.
- Compare only jobs with the same vehicle ID.
- Reject duplicate IDs or malformed jobs with ValueError.

### Hints
1. For each pair, compare only when vehicle IDs match.
2. Two half-open intervals overlap when each starts before the other ends.
3. Keep the original pair order.

### Common Mistakes
- Treating touching intervals as overlapping.
- Comparing jobs from different vehicles.
- Returning reversed or sorted pairs.

### Extension Challenge
Return each conflict with its overlap duration in minutes.
