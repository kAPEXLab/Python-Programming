# 15 - Parts Inventory - Difficult

## Question Details
- Concept: Dictionary aggregation
- Supporting concepts: Nested records, validation, sorting, rounding, functions
- Difficulty: Difficult
- Domain: Simulated parts inventory report
- Learning Objective: Aggregate quantities and values from nested inventory records into a deterministic report.

## Scenario
An offline parts fixture contains repeated records for part numbers, unit prices, and quantities.

## Function Details
- Function signature: `summarize_parts_inventory(records: list[dict[str, object]]) -> dict[str, object]`
- Behavior / return shape: Combine duplicate parts and identify the highest-value inventory item.
- Exact accepted inputs: Each record has non-empty string `part_number`, positive finite `unit_price` from 0.01 through 100000.0, and integer `quantity` from 1 through 10000. A part must always use the same unit price.
- Output and validation / behavior: Return `quantities` as a dictionary by part number, `total_value` rounded to two decimals, and `highest_value_part` as the lexicographically smallest part on ties, or `None` for empty input.

## Tasks to Implement
1. Implement `summarize_parts_inventory` with the exact signature above and validate the inputs against these accepted rules: Each record has non-empty string `part_number`, positive finite `unit_price` from 0.01 through 100000.0, and integer `quantity` from 1 through 10000. A part must always use the same unit price.
2. Combine duplicate parts and identify the highest-value inventory item.
3. Implement this output contract exactly: Return `quantities` as a dictionary by part number, `total_value` rounded to two decimals, and `highest_value_part` as the lexicographically smallest part on ties, or `None` for empty input.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | summarize_parts_inventory([{"part_number": "A", "unit_price": 10, "quantity": 2}]) | {"quantities": {"A": 2}, "total_value": 20.0, "highest_value_part": "A"} | Typical valid input. |
| 2 | summarize_parts_inventory([{"part_number": "B", "unit_price": 0.01, "quantity": 1}]) | {"quantities": {"B": 1}, "total_value": 0.01, "highest_value_part": "B"} | Valid boundary case. |
| 3 | summarize_parts_inventory([{"part_number": "B", "unit_price": 5, "quantity": 2}, {"part_number": "A", "unit_price": 5, "quantity": 2}]) | {"quantities": {"B": 2, "A": 2}, "total_value": 20.0, "highest_value_part": "A"} | Checks the threshold rule. |
| 4 | summarize_parts_inventory([{"part_number": "X", "unit_price": 100000, "quantity": 10000}]) | {"quantities": {"X": 10000}, "total_value": 1000000000.0, "highest_value_part": "X"} | Checks an alternate valid shape. |
| 5 | summarize_parts_inventory([]) | {"quantities": {}, "total_value": 0.0, "highest_value_part": None} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of summarize_parts_inventory that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Dictionaries, lists, loops, arithmetic, sorting, and validation.

### Rules and Constraints
- Aggregate quantity before calculating each part's value.
- Reject malformed records or conflicting prices with ValueError.
- Do not mutate records.

### Hints
1. Track quantity and unit price separately by part.
2. Compute value after aggregation.
3. Use a stable key rule when values tie.

### Common Mistakes
- Calculating only the last duplicate quantity.
- Rounding each line before totaling.
- Choosing a nondeterministic tie result.

### Extension Challenge
Return all parts sorted by descending inventory value and then part number.
