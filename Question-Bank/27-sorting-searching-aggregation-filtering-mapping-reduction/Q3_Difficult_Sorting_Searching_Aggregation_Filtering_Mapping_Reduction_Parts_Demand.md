# 27 - Sorting Searching Aggregation Filtering Mapping Reduction Parts Demand - Difficult

## Question Details
- **Concept:** Sorting, searching, aggregation, filtering, mapping, and reduction
- **Supporting Python concepts:** Grouping, thresholds, key functions
- **Difficulty:** Difficult
- **Domain:** Offline parts-demand report
- **Learning Objective:** Aggregate work-order quantities and select parts that meet a demand threshold.
- **Estimated completion time:** 55 minutes

## Scenario
A parts planner has completed work-order lines and wants the most requested components.

## Function Details
Implement `parts_demand(lines: list[dict[str, object]], minimum_quantity: int) -> list[tuple[str, int]]`.

**Required API / operation:** Sum quantities by part and return only parts whose total meets the threshold.

**Input rules and constraints:** Each line has `part` (non-empty string) and `quantity` (integer from 1 through 1000). The threshold is an integer from 1 through 10000.

**Behavior and return shape:** Return `(part, total_quantity)` tuples sorted by total descending, then part ascending. Include totals greater than or equal to the threshold.

**Implementation rules:** Reject booleans and malformed records. Do not mutate input. Return `[]` when no part reaches the threshold.

## Tasks to Implement
1. Aggregate work-order quantities and select parts that meet a demand threshold.
2. Sum quantities by part and return only parts whose total meets the threshold.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `lines=[{"part":"A","quantity":1}], minimum_quantity=1` | `[('A', 1)]` |
| 2 | `lines=[{"part":"B","quantity":2},{"part":"B","quantity":3}], minimum_quantity=5` | `[('B', 5)]` |
| 3 | `lines=[{"part":"B","quantity":5},{"part":"A","quantity":5}], minimum_quantity=5` | `[('A', 5), ('B', 5)]` |
| 4 | `lines=[{"part":"X","quantity":1},{"part":"Y","quantity":2}], minimum_quantity=4` | `[]` |
| 5 | `lines=[{"part":"A","quantity":1000},{"part":"A","quantity":1000}], minimum_quantity=2000` | `[('A', 2000)]` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Dictionaries, loops, comprehensions, sorting, and validation.

### Rules and Constraints
- Reject booleans and malformed records.
- Do not mutate input.
- Return `[]` when no part reaches the threshold.

### Hints
1. Reduce quantities into a dictionary.
2. Filter dictionary items by threshold.
3. Sort tuples with negative quantity as the primary key.

### Common Mistakes
- Filtering individual lines instead of totals.
- Excluding totals equal to the threshold.
- Sorting part names before demand.

### Extension Challenge
Return the top three parts and their percentage of total demand.
