# 20 - Variadic Arguments Lambda and Higher Order Functions Parts Sorting - Medium

## Question Details
- **Concept:** Higher-order functions and key lambdas
- **Supporting Python concepts:** `*args`, tuples, stable sorting, validation
- **Difficulty:** Medium
- **Domain:** Offline parts sorting
- **Learning Objective:** Sort a variable number of part records using a lambda key and deterministic tie behavior.
- **Estimated completion time:** 40 minutes

## Scenario
A simulated workshop receives part records as `(part_number, price)` tuples.

## Function Details
Implement `sort_parts(*parts: tuple[str, float]) -> list[tuple[str, float]]`.

**Required API / operation:** Return parts ordered by price ascending, then part number alphabetically.

**Input rules and constraints:** Each part number is 1 to 20 uppercase alphanumeric or hyphen characters after trimming. Prices are finite numbers from 0.01 through 100000.0.

**Behavior and return shape:** Return a new list sorted by `(price, normalized_part_number)`. Normalize part numbers to uppercase and round prices to two decimals in the output.

**Implementation rules:** Use a lambda as the sort key. Preserve duplicate records and do not mutate input tuples. Raise `ValueError` for malformed parts.

## Tasks to Implement
1. Sort a variable number of part records using a lambda key and deterministic tie behavior.
2. Return parts ordered by price ascending, then part number alphabetically.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `parts=("AB-1", 10.0), ("CD-2", 5.0)` | `[('CD-2', 5.0), ('AB-1', 10.0)]` |
| 2 | `parts=("z-1", 5.0), ("A-1", 5.0)` | `[('A-1', 5.0), ('Z-1', 5.0)]` |
| 3 | `parts=("AB-1", 0.01)` | `[('AB-1', 0.01)]` |
| 4 | `parts=("AB-1", 10.126), ("AB-2", 10.1)` | `[('AB-2', 10.1), ('AB-1', 10.13)]` |
| 5 | `parts=("AA", 100000.0), ("AA", 100000.0)` | `[('AA', 100000.0), ('AA', 100000.0)]` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, `*args`, tuples, lambdas, sorting, and validation.

### Rules and Constraints
- Use a lambda as the sort key.
- Preserve duplicate records and do not mutate input tuples.
- Raise `ValueError` for malformed parts.

### Hints
1. Normalize and validate before sorting.
2. Use a two-item tuple as the lambda key.
3. Keep the returned records separate from the input records.

### Common Mistakes
- Sorting by part number before price.
- Letting input case affect ties.
- Returning a tuple of records instead of a list.

### Extension Challenge
Add a keyword-only `reverse_price` option without reversing alphabetical tie order.
