# 04 - VIN Display - Easy

## Question Details
- Concept: Strings
- Supporting concepts: String methods, validation, formatting
- Difficulty: Easy
- Domain: Vehicle identification number (VIN) display
- Learning Objective: Normalize and validate a vehicle identifier using basic string operations.

## Scenario
A VIN is a 17-character identifier for a vehicle. This exercise uses a simplified rule: the VIN may contain uppercase letters and digits, but not spaces or punctuation.

## Function Details
- Function signature: `format_vin(vin: str) -> str`
- Behavior / return shape: Normalize a VIN and display it in grouped blocks for a workshop screen.
- Exact accepted inputs: `vin` must normalize to exactly 17 uppercase letters or digits. Reject invalid input with `ValueError`.
- Output and validation / behavior: Return the normalized 17-character VIN grouped as 4, 4, 4, and 5 characters separated by hyphens, for example `WVWZ-ZZ1J-ZXW0-00001`.

## Tasks to Implement
1. Implement `format_vin` with the exact signature above and validate the inputs against these accepted rules: `vin` must normalize to exactly 17 uppercase letters or digits. Reject invalid input with `ValueError`.
2. Normalize a VIN and display it in grouped blocks for a workshop screen.
3. Implement this output contract exactly: Return the normalized 17-character VIN grouped as 4, 4, 4, and 5 characters separated by hyphens, for example `WVWZ-ZZ1J-ZXW0-00001`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | format_vin("wvwzzz1jzxw000001") | WVWZ-ZZ1J-ZXW0-00001 | Typical valid input. |
| 2 | format_vin("1hgcm82633a004352") | 1HGC-M826-33A0-04352 | Valid lower or upper boundary. |
| 3 | format_vin(" 5YJSA1E26HF000001 ") | 5YJS-A1E2-6HF0-00001 | Checks the threshold rule. |
| 4 | format_vin("ABCDEFGHIJKLMN123") | ABCD-EFGH-IJKL-MN123 | Checks a second valid shape or aggregate. |
| 5 | format_vin("12345678901234567") | 1234-5678-9012-34567 | Checks another valid contract case. |

## Expected Deliverables
- Complete implementation of format_vin that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Strings, methods, conditionals, functions, and formatted output.

### Rules and Constraints
- Use string methods and a clear function.
- Do not silently remove internal spaces or punctuation.
- Preserve digits.

### Hints
1. Normalize only outer whitespace and case.
2. Validate length and allowed characters.
3. Use slices to create four groups.

### Common Mistakes
- Removing internal spaces.
- Producing groups of equal length.
- Forgetting lowercase input.

### Extension Challenge
Mask characters 9 through 12 with * for a privacy-safe display.
