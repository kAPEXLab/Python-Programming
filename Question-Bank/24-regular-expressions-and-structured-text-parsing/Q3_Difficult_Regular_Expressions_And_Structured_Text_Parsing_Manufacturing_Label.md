# 24 - Regular Expressions and Structured Text Parsing Manufacturing Label - Difficult

## Question Details
- **Concept:** Regular expressions and structured text parsing
- **Supporting Python concepts:** Optional groups, dates, normalization
- **Difficulty:** Difficult
- **Domain:** Offline component manufacturing labels
- **Learning Objective:** Parse a compact label containing required and optional manufacturing fields.
- **Estimated completion time:** 50 minutes

## Scenario
A test fixture receives labels in the form `PART:BP-042;LOT:2026A17;REV:03;DATE:2026-08-26`.

## Function Details
Implement `parse_manufacturing_label(label: str) -> dict[str, str]`.

**Required API / operation:** Extract the four label fields and normalize their values for inventory inspection.

**Input rules and constraints:** Fields must appear exactly in the order `PART`, `LOT`, `REV`, `DATE`, separated by semicolons. Part is 2 to 10 uppercase letters, digits, or hyphens; lot is 4 to 12 alphanumeric characters; revision is two digits; date is ISO `YYYY-MM-DD`.

**Behavior and return shape:** Return lowercase keys `part`, `lot`, `revision`, and `date`, preserving field values except for trimming surrounding whitespace.

**Implementation rules:** Use one anchored regular expression with named groups. Reject unknown fields, missing fields, and invalid separators with `ValueError`. Date shape must be validated; calendar validity may be checked with `datetime`.

## Tasks to Implement
1. Parse a compact label containing required and optional manufacturing fields.
2. Extract the four label fields and normalize their values for inventory inspection.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `label="PART:BP-042;LOT:2026A17;REV:03;DATE:2026-08-26"` | `{'part': 'BP-042', 'lot': '2026A17', 'revision': '03', 'date': '2026-08-26'}` |
| 2 | `label="PART:AB;LOT:A123;REV:00;DATE:2000-02-29"` | `{'part': 'AB', 'lot': 'A123', 'revision': '00', 'date': '2000-02-29'}` |
| 3 | `label="PART:BATTERY-1;LOT:1234;REV:99;DATE:2024-02-29"` | `{'part': 'BATTERY-1', 'lot': '1234', 'revision': '99', 'date': '2024-02-29'}` |
| 4 | `label=" PART:BP-042 ; LOT:2026A17 ; REV:03 ; DATE:2026-08-26 "` | `{'part': 'BP-042', 'lot': '2026A17', 'revision': '03', 'date': '2026-08-26'}` |
| 5 | `label="PART:EV-9;LOT:AB12;REV:10;DATE:2026-01-01"` | `{'part': 'EV-9', 'lot': 'AB12', 'revision': '10', 'date': '2026-01-01'}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Regular expressions, strings, dictionaries, and validation.

### Rules and Constraints
- Use one anchored regular expression with named groups.
- Reject unknown fields, missing fields, and invalid separators with `ValueError`.
- Date shape must be validated; calendar validity may be checked with `datetime`.

### Hints
1. Escape literal punctuation in the pattern.
2. Use named groups for readable result construction.
3. Anchor both ends of the label.

### Common Mistakes
- Accepting fields in any order.
- Converting revision `00` to integer zero.
- Using a loose search instead of a full match.

### Extension Challenge
Support an optional `COLOR` field only after `DATE`, returning it when present.
