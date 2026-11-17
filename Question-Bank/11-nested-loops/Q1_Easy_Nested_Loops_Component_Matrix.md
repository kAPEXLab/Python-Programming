# 11 - Component Matrix - Easy

## Question Details
- Concept: Nested for loops
- Supporting concepts: Lists, strings, validation, counting
- Difficulty: Easy
- Domain: Component inspection matrix
- Learning Objective: Use nested loops to inspect every cell in a two-dimensional test matrix.

## Scenario
A factory checks rows of vehicles against columns of inspection items. Each cell contains PASS or FAIL.

## Function Details
- Function signature: `count_matrix_failures(matrix: list[list[str]]) -> dict[str, int]`
- Behavior / return shape: Count total cells and failed cells in the matrix.
- Exact accepted inputs: The matrix has 0 to 100 rows. Each row has 0 to 100 cells, and all rows must have equal length. Cells are case-insensitive `PASS` or `FAIL`. Reject ragged or invalid matrices with `ValueError`.
- Output and validation / behavior: Return `total_checks` and `failed_checks`.

## Tasks to Implement
1. Implement `count_matrix_failures` with the exact signature above and validate the inputs against these accepted rules: The matrix has 0 to 100 rows. Each row has 0 to 100 cells, and all rows must have equal length. Cells are case-insensitive `PASS` or `FAIL`. Reject ragged or invalid matrices with `ValueError`.
2. Count total cells and failed cells in the matrix.
3. Implement this output contract exactly: Return `total_checks` and `failed_checks`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | count_matrix_failures([["PASS"]]) | {"total_checks": 1, "failed_checks": 0} | Typical valid input. |
| 2 | count_matrix_failures([["FAIL"]]) | {"total_checks": 1, "failed_checks": 1} | Valid boundary case. |
| 3 | count_matrix_failures([["PASS", "FAIL"], ["FAIL", "PASS"]]) | {"total_checks": 4, "failed_checks": 2} | Checks the threshold rule. |
| 4 | count_matrix_failures([[], []]) | {"total_checks": 0, "failed_checks": 0} | Checks an alternate valid shape. |
| 5 | count_matrix_failures([]) | {"total_checks": 0, "failed_checks": 0} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of count_matrix_failures that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, loops, booleans, functions, and validation.

### Rules and Constraints
- Use two nested for loops.
- An empty matrix returns both counts as zero.
- Do not mutate input.

### Hints
1. Validate row lengths before counting.
2. Outer loop handles rows; inner loop handles cells.
3. Normalize each cell before comparison.

### Common Mistakes
- Checking only the first row.
- Accepting ragged rows.
- Counting lowercase labels as invalid.

### Extension Challenge
Return the zero-based coordinates of every failed cell.
