# 21 - Recursion Charging Plan - Difficult

## Question Details
- **Concept:** Recursive backtracking
- **Supporting Python concepts:** Tuples, constraints, search, validation, deterministic choice
- **Difficulty:** Difficult
- **Domain:** Simulated charging plan selection
- **Learning Objective:** Use recursion and backtracking to select charging sessions that reach a target energy with minimum session count.
- **Estimated completion time:** 60 minutes

## Scenario
An offline planner has fixed charging session options measured in kWh. Each option can be used at most once.

## Function Details
Implement `plan_charging(target_kwh: int, sessions: list[int]) -> tuple[int, ...] | None`.

**Required API / operation:** Find an exact combination of sessions that reaches the target energy using the fewest sessions.

**Input rules and constraints:** Target is an integer from 0 through 500. Sessions contain 0 through 30 unique positive integers from 1 through 500. Every value is measured in whole kWh.

**Behavior and return shape:** Return a tuple of selected session values whose sum equals target and whose length is minimal. Return `None` when no exact combination exists. For ties, return the lexicographically smallest sorted tuple. Target zero returns `()`.

**Implementation rules:** Use recursive backtracking; each session can be selected once. Do not mutate the input list. Validate all values and keep results deterministic.

## Tasks to Implement
1. Use recursion and backtracking to select charging sessions that reach a target energy with minimum session count.
2. Find an exact combination of sessions that reaches the target energy using the fewest sessions.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `target_kwh=0, sessions=[]` | `()` |
| 2 | `target_kwh=5, sessions=[5]` | `(5,)` |
| 3 | `target_kwh=10, sessions=[6, 4, 10]` | `(10,)` |
| 4 | `target_kwh=10, sessions=[6, 4, 5, 5]` | `(4, 6)` |
| 5 | `target_kwh=7, sessions=[2, 4]` | `None` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Recursion, lists, tuples, arithmetic, sorting, and validation.

### Rules and Constraints
- Use recursive backtracking; each session can be selected once.
- Do not mutate the input list.
- Validate all values and keep results deterministic.

### Hints
1. Define a recursive search with a start index and remaining target.
2. Track the best valid combination rather than stopping at the first one.
3. Sort candidate tuples before applying the tie-break rule.

### Common Mistakes
- Reusing a session more than once.
- Returning a non-minimal combination.
- Treating an impossible target as an exception.

### Extension Challenge
Add a maximum available charging time per session and optimize total time after session count.
