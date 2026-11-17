# 38 - Normalizing Diagnostic Trouble Codes - Medium

## Question Details
- **Concept:** Raising and defining custom exceptions
- **Supporting Python concepts:** Regular expressions, exception payloads, parsing, validation
- **Difficulty:** Medium
- **Domain:** Offline diagnostic trouble code validation
- **Learning Objective:** Create a custom validation exception and use it to protect a diagnostic-code parser.

## Scenario
A diagnostic report accepts standardized DTC-like codes but must identify malformed entries clearly.

## Function Details
- **Required Python interface:** Define `InvalidDTC(Exception)` and implement `normalize_dtc(raw: str) -> str`.
- **Behavior:** Strip surrounding whitespace, uppercase the code, and accept exactly one letter from `P`, `B`, `C`, or `U` followed by four hexadecimal characters. Raise `InvalidDTC` with the original input for any failure.
- **Return shape:** Return the normalized uppercase code.
- **Input rules and constraints:** Input must be a string. Valid examples include `p0420` and `U0100`. Additional constraints: Preserve the original invalid value in the exception; Do not accept internal whitespace or six-character codes; Do not query a real diagnostic interface.

## Tasks to Implement
1. Implement the specified Python interface: Define `InvalidDTC(Exception)` and implement `normalize_dtc(raw: str) -> str`.
2. Apply the stated input validation and constraints: Input must be a string. Valid examples include `p0420` and `U0100`.
3. Implement the required behavior: Strip surrounding whitespace, uppercase the code, and accept exactly one letter from `P`, `B`, `C`, or `U` followed by four hexadecimal characters. Raise `InvalidDTC` with the original input for any failure.
4. Return the specified result shape without changing the required ordering or formatting: Return the normalized uppercase code.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `normalize_dtc("p0420")` | `"P0420"` |
| 2 | `normalize_dtc(" U0100 ")` | `"U0100"` |
| 3 | `normalize_dtc("b00af")` | `"B00AF"` |
| 4 | `normalize_dtc("c1234")` | `"C1234"` |
| 5 | `normalize_dtc("u0a0f")` | `"U0A0F"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Exceptions, classes, strings, regular expressions, and functions.

### Rules and Constraints

- Preserve the original invalid value in the exception.
- Do not accept internal whitespace or six-character codes.
- Do not query a real diagnostic interface.

### Hints

Compile one anchored regular expression and match the normalized value.

### Common Mistakes

- Accepting arbitrary letters.
- Removing internal spaces.
- Losing the original input in the exception.

### Extension Challenge

Add a parsed `system` property to the exception.
