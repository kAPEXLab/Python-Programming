# 24 - Regular Expressions and Structured Text Parsing CAN Text Dump - Medium

## Question Details
- **Concept:** Regular expressions and structured text parsing
- **Supporting Python concepts:** Repeated records, hexadecimal validation, list results
- **Difficulty:** Medium
- **Domain:** Offline CAN text dump parsing
- **Learning Objective:** Extract repeated hexadecimal CAN frames from structured text.
- **Estimated completion time:** 55 minutes

## Scenario
A simulator exports frames as `ID=7E8 DLC=3 DATA=01 0A FF`, one frame per line.

## Function Details
Implement `parse_can_dump(text: str) -> list[dict[str, object]]`.

**Required API / operation:** Parse every valid frame in a dump and preserve input order.

**Input rules and constraints:** Each non-empty line must contain an uppercase or lowercase hexadecimal ID from 1 to 3 digits, DLC from 0 to 8, and exactly DLC two-digit hexadecimal data bytes separated by spaces.

**Behavior and return shape:** Return dictionaries with integer `can_id`, integer `dlc`, and list[int] `data`. Raise `ValueError` if any non-empty line is invalid.

**Implementation rules:** Use a regular expression to validate and capture each line. `DLC=0` must have an empty data list. Do not interpret the input as a live bus connection.

## Tasks to Implement
1. Extract repeated hexadecimal CAN frames from structured text.
2. Parse every valid frame in a dump and preserve input order.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `text="ID=7E8 DLC=3 DATA=01 0A FF"` | `[{'can_id': 2024, 'dlc': 3, 'data': [1, 10, 255]}]` |
| 2 | `text="ID=1 DLC=0 DATA="` | `[{'can_id': 1, 'dlc': 0, 'data': []}]` |
| 3 | `text="ID=7e8 DLC=2 DATA=0a ff"` | `[{'can_id': 2024, 'dlc': 2, 'data': [10, 255]}]` |
| 4 | `text="ID=123 DLC=1 DATA=AB\nID=456 DLC=2 DATA=01 02"` | `[{'can_id': 291, 'dlc': 1, 'data': [171]}, {'can_id': 1110, 'dlc': 2, 'data': [1, 2]}]` |
| 5 | `text="\nID=7FF DLC=1 DATA=00\n"` | `[{'can_id': 2047, 'dlc': 1, 'data': [0]}]` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Regular expressions, lists, dictionaries, loops, and validation.

### Rules and Constraints
- Use a regular expression to validate and capture each line.
- `DLC=0` must have an empty data list.
- Do not interpret the input as a live bus connection.

### Hints
1. Process lines with `splitlines`.
2. Capture the data text separately, then split bytes.
3. Compare byte count with the captured DLC.

### Common Mistakes
- Accepting non-hex bytes.
- Returning hexadecimal strings instead of integers.
- Treating blank lines as frames.

### Extension Challenge
Add an optional timestamp prefix while retaining support for the original format.
