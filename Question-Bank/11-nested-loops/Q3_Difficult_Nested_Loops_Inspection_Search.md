# 11 - Inspection Search - Difficult

## Question Details
- Concept: Nested loops with loop else
- Supporting concepts: Searching, validation, early exit, dictionaries
- Difficulty: Difficult
- Domain: Manufacturing inspection search
- Learning Objective: Search a multi-level inspection report and distinguish found, not-found, and invalid outcomes using nested loops and loop else.

## Scenario
A manufacturing report groups inspection records by vehicle. Each record has a component and status. Engineers need to find the first vehicle containing a specified failed component.

## Function Details
- Function signature: `find_first_failed_component(report: list[dict[str, object]], component_name: str) -> str | None`
- Behavior / return shape: Search vehicles in input order and components in each vehicle's input order.
- Exact accepted inputs: Up to 10,000 vehicles and 100 checks per vehicle; IDs and component names are non-empty strings; Status is `PASS` or `FAIL`, case-insensitive; Component search is case-insensitive after trimming; Reject malformed records with `ValueError`.
- Output and validation / behavior: Return the first matching vehicle ID, or `None` after a complete search. A component with `PASS` does not match.

## Tasks to Implement
1. Implement `find_first_failed_component` with the exact signature above and validate the inputs against these accepted rules: Up to 10,000 vehicles and 100 checks per vehicle; IDs and component names are non-empty strings; Status is `PASS` or `FAIL`, case-insensitive; Component search is case-insensitive after trimming; Reject malformed records with `ValueError`.
2. Search vehicles in input order and components in each vehicle's input order.
3. Implement this output contract exactly: Return the first matching vehicle ID, or `None` after a complete search. A component with `PASS` does not match.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | find_first_failed_component([{"vehicle_id": "V1", "checks": [{"component": "brake", "status": "FAIL"}]}], "brake") | V1 | Typical valid input. |
| 2 | find_first_failed_component([{"vehicle_id": "V1", "checks": [{"component": "brake", "status": "PASS"}]}, {"vehicle_id": "V2", "checks": [{"component": "brake", "status": "FAIL"}]}], "BRAKE") | V2 | Valid boundary case. |
| 3 | find_first_failed_component([{"vehicle_id": "V1", "checks": []}], "engine") | None | Checks the threshold rule. |
| 4 | find_first_failed_component([{"vehicle_id": "A", "checks": [{"component": "engine", "status": "FAIL"}]}, {"vehicle_id": "B", "checks": [{"component": "engine", "status": "FAIL"}]}], " engine ") | A | Checks an alternate valid shape. |
| 5 | find_first_failed_component([], "brake") | None | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of find_first_failed_component that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Nested loops, loop else, dictionaries, strings, validation, and exceptions.

### Rules and Constraints
- Use nested loops.
- Use loop else on at least the inner or outer search loop to represent no match.
- Stop after the first matching vehicle.
- Do not mutate input.

### Hints
1. Normalize the requested component once.
2. Track whether the inner search found a failed matching check.
3. Use break to stop both searches at the first vehicle match.

### Common Mistakes
- Returning a vehicle for a matching component that passed.
- Continuing after a match.
- Forgetting to validate nested checks.
- Misusing loop else so it runs after a successful break.

### Extension Challenge
Return the vehicle ID and component-check index as a tuple.
