# 14 - Unique Fault Codes - Easy

## Question Details
- Concept: Sets and uniqueness
- Supporting concepts: Strings, normalization, validation, functions
- Difficulty: Easy
- Domain: Offline diagnostic fault codes
- Learning Objective: Use a set to count unique normalized fault codes.

## Scenario
A simulated scan may report the same diagnostic trouble code several times.

## Function Details
- Function signature: `unique_fault_codes(codes: list[str]) -> dict[str, object]`
- Behavior / return shape: Return the unique codes in uppercase and the number of distinct codes.
- Exact accepted inputs: The list has 0 through 1,000 non-empty strings. Codes may contain letters, digits, and hyphens, and surrounding whitespace is allowed.
- Output and validation / behavior: Return `unique_codes` as a set of uppercase trimmed codes and `unique_count` as its size.

## Tasks to Implement
1. Implement `unique_fault_codes` with the exact signature above and validate the inputs against these accepted rules: The list has 0 through 1,000 non-empty strings. Codes may contain letters, digits, and hyphens, and surrounding whitespace is allowed.
2. Return the unique codes in uppercase and the number of distinct codes.
3. Implement this output contract exactly: Return `unique_codes` as a set of uppercase trimmed codes and `unique_count` as its size.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | unique_fault_codes(["P1", "p1", " B2 "]) | {"unique_codes": {"P1", "B2"}, "unique_count": 2} | Typical valid input. |
| 2 | unique_fault_codes([]) | {"unique_codes": set(), "unique_count": 0} | Valid boundary case. |
| 3 | unique_fault_codes(["A-1", "b-2"]) | {"unique_codes": {"A-1", "B-2"}, "unique_count": 2} | Checks the threshold rule. |
| 4 | unique_fault_codes(["XYZ"]) | {"unique_codes": {"XYZ"}, "unique_count": 1} | Checks an alternate valid shape. |
| 5 | unique_fault_codes(["1", "1", "2", "3"]) | {"unique_codes": {"1", "2", "3"}, "unique_count": 3} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of unique_fault_codes that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, strings, sets, functions, and exceptions.

### Rules and Constraints
- Use a set for uniqueness.
- Reject empty or malformed codes with ValueError.
- Do not mutate input.

### Hints
1. Strip and uppercase each code.
2. Add normalized values to a set.
3. Check allowed characters before insertion.

### Common Mistakes
- Counting list entries instead of unique values.
- Forgetting whitespace normalization.
- Returning a sorted list when a set is requested.

### Extension Challenge
Return a dictionary mapping each normalized code to its occurrence count.
