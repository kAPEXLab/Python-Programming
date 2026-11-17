# 20 - Variadic Arguments Lambda and Higher Order Functions Telemetry Filters - Easy

## Question Details
- **Concept:** `*args` and lambda expressions
- **Supporting Python concepts:** Filtering, functions, validation, sorting
- **Difficulty:** Easy
- **Domain:** Simulated telemetry filters
- **Learning Objective:** Accept a variable number of readings and use a lambda-based predicate to filter them.
- **Estimated completion time:** 30 minutes

## Scenario
An offline dashboard receives a flexible number of speed readings for one display window.

## Function Details
Implement `filter_speeds(threshold_kmh: int, *readings_kmh: int) -> list[int]`.

**Required API / operation:** Return readings at or above a supplied threshold in ascending order.

**Input rules and constraints:** Threshold and readings are integers from 0 through 240; booleans are invalid. Zero readings are allowed.

**Behavior and return shape:** Use a lambda predicate with `filter` or an equivalent higher-order operation, then return qualifying readings sorted ascending.

**Implementation rules:** Preserve no duplicate removal; repeated readings remain repeated. Raise `ValueError` for invalid values. Do not mutate arguments.

## Tasks to Implement
1. Accept a variable number of readings and use a lambda-based predicate to filter them.
2. Return readings at or above a supplied threshold in ascending order.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `threshold_kmh=0 (no readings)` | `[]` |
| 2 | `threshold_kmh=100, readings=(90, 100, 120)` | `[100, 120]` |
| 3 | `threshold_kmh=240, readings=(240, 240)` | `[240, 240]` |
| 4 | `threshold_kmh=50, readings=(80, 20, 50)` | `[50, 80]` |
| 5 | `threshold_kmh=120, readings=(120, 0, 119)` | `[120]` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, `*args`, lambdas, lists, comparisons, and validation.

### Rules and Constraints
- Preserve no duplicate removal; repeated readings remain repeated.
- Raise `ValueError` for invalid values.
- Do not mutate arguments.

### Hints
1. Validate the threshold and every variadic reading.
2. Build a predicate that compares one reading with the threshold.
3. Sort only the result.

### Common Mistakes
- Treating the first reading as the threshold.
- Removing duplicates with a set.
- Sorting the input tuple in place.

### Extension Challenge
Accept a keyword-only `descending` flag and reverse the result when true.
