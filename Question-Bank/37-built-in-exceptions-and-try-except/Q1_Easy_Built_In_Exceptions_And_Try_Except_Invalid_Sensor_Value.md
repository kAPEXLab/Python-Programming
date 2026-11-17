# 37 - Parsing Sensor Temperatures Safely - Easy

## Question Details
- **Concept:** Built-in exceptions and try-except
- **Supporting Python concepts:** Parsing, validation, loops, error reporting
- **Difficulty:** Easy
- **Domain:** Offline sensor packet parsing
- **Learning Objective:** Convert untrusted sensor text while handling expected built-in exceptions.

## Scenario
A simulated packet contains textual temperature values that may be malformed.

## Function Details
- **Required Python interface:** Implement `parse_temperatures(raw_values: list[str]) -> tuple[list[float], list[str]]`, converting Celsius strings and collecting invalid entries.
- **Behavior:** Strip whitespace, convert with `float`, accept values from -50 through 150 inclusive, and round valid results to one decimal place. Invalid entries are returned unchanged in the error list.
- **Return shape:** Return `(valid_values, invalid_values)` preserving input order within each list.
- **Input rules and constraints:** The input list may be empty. Items should normally be strings; non-strings are invalid entries. Additional constraints: Catch expected conversion and type errors without hiding programming errors; Never stop processing after one bad value; Use Python 3.12+.

## Tasks to Implement
1. Implement the specified Python interface: Implement `parse_temperatures(raw_values: list[str]) -> tuple[list[float], list[str]]`, converting Celsius strings and collecting invalid entries.
2. Apply the stated input validation and constraints: The input list may be empty. Items should normally be strings; non-strings are invalid entries.
3. Implement the required behavior: Strip whitespace, convert with `float`, accept values from -50 through 150 inclusive, and round valid results to one decimal place. Invalid entries are returned unchanged in the error list.
4. Return the specified result shape without changing the required ordering or formatting: Return `(valid_values, invalid_values)` preserving input order within each list.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `parse_temperatures(["20", "bad", "150"])` | `([20.0, 150.0], ["bad"])` |
| 2 | `parse_temperatures([])` | `([], [])` |
| 3 | `parse_temperatures([" -50.04 ", "151"])` | `([-50.0], ["151"])` |
| 4 | `parse_temperatures(["0", "0.05", "-0.05"])` | `([0.0, 0.1, -0.1], [])` |
| 5 | `parse_temperatures(["nan", "inf", "25.55"])` | `([25.6], ["nan", "inf"])` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Functions, strings, lists, `try-except`, and `ValueError`.

### Rules and Constraints

- Catch expected conversion and type errors without hiding programming errors.
- Never stop processing after one bad value.
- Use Python 3.12+.

### Hints

Keep conversion and range validation inside the loop.

### Common Mistakes

- Catching every exception with a bare `except`.
- Returning converted out-of-range values.
- Losing the original invalid text.

### Extension Challenge

Return an error dictionary containing index and reason.
