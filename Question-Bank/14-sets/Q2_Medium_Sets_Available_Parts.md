# 14 - Available Parts - Medium

## Question Details
- Concept: Set difference and intersection
- Supporting concepts: Strings, normalization, validation, functions
- Difficulty: Medium
- Domain: Simulated workshop parts availability
- Learning Objective: Use set operations to identify requested parts that are unavailable.

## Scenario
A workshop simulation compares parts requested for a service job with the parts currently on hand.

## Function Details
- Function signature: `check_parts_availability(requested: list[str], available: list[str]) -> dict[str, object]`
- Behavior / return shape: Return the missing parts, available requested parts, and whether the job can start.
- Exact accepted inputs: Each list has 0 through 500 non-empty part names. Names use letters, digits, and hyphens; matching is case-insensitive after trimming.
- Output and validation / behavior: Return `missing` as `requested_set - available_set`, `available_requested` as their intersection, and `ready` as whether missing is empty. Values must be normalized uppercase sets.

## Tasks to Implement
1. Implement `check_parts_availability` with the exact signature above and validate the inputs against these accepted rules: Each list has 0 through 500 non-empty part names. Names use letters, digits, and hyphens; matching is case-insensitive after trimming.
2. Return the missing parts, available requested parts, and whether the job can start.
3. Implement this output contract exactly: Return `missing` as `requested_set - available_set`, `available_requested` as their intersection, and `ready` as whether missing is empty. Values must be normalized uppercase sets.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | check_parts_availability(["A", "B"], ["A"]) | {"missing": {"B"}, "available_requested": {"A"}, "ready": False} | Typical valid input. |
| 2 | check_parts_availability([], []) | {"missing": set(), "available_requested": set(), "ready": True} | Valid boundary case. |
| 3 | check_parts_availability(["A", "B"], ["A", "B"]) | {"missing": set(), "available_requested": {"A", "B"}, "ready": True} | Checks the threshold rule. |
| 4 | check_parts_availability(["x-1", "Y"], ["X-1"]) | {"missing": {"Y"}, "available_requested": {"X-1"}, "ready": False} | Checks an alternate valid shape. |
| 5 | check_parts_availability(["P1", "P2", "P3"], ["p2", "p4"]) | {"missing": {"P1", "P3"}, "available_requested": {"P2"}, "ready": False} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of check_parts_availability that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Sets, lists, strings, functions, and validation.

### Rules and Constraints
- Use set difference and intersection operators.
- Duplicate entries do not affect results.
- Raise ValueError for malformed names and do not mutate lists.

### Hints
1. Normalize each list into a set.
2. Difference finds requested items absent from stock.
3. Use not missing for the readiness flag.

### Common Mistakes
- Treating duplicates as separate inventory.
- Comparing names before normalization.
- Reporting unrelated available stock as requested.

### Extension Challenge
Return the missing parts in deterministic sorted-list form as an additional field.
