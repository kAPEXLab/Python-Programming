# 23 - String Methods and Formatting VIN Normalization - Easy

## Question Details
- **Concept:** String methods and formatting
- **Supporting Python concepts:** Validation, slicing, case conversion
- **Difficulty:** Easy
- **Domain:** Offline vehicle identification display
- **Learning Objective:** Normalize a vehicle identification string while applying strict character and length rules.
- **Estimated completion time:** 35 minutes

## Scenario
A simulated inventory screen receives VIN text from multiple operators with inconsistent spacing and case.

## Function Details
Implement `normalize_vin(raw_vin: str) -> str`.

**Required API / operation:** Return a display-ready VIN after trimming separators and uppercasing letters.

**Input rules and constraints:** The input may contain surrounding whitespace and internal hyphens or spaces. After removing spaces and hyphens, it must contain exactly 17 uppercase letters or digits, excluding `I`, `O`, and `Q`.

**Behavior and return shape:** Return the 17-character uppercase VIN with separators removed.

**Implementation rules:** Accept only a string. Do not use external VIN services. Raise `ValueError` for invalid length or characters.

## Tasks to Implement
1. Normalize a vehicle identification string while applying strict character and length rules.
2. Return a display-ready VIN after trimming separators and uppercasing letters.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `raw_vin="1HGCM82633A004352"` | `'1HGCM82633A004352'` |
| 2 | `raw_vin="1hgcm82633a004352"` | `'1HGCM82633A004352'` |
| 3 | `raw_vin="1HG CM82633-A004352"` | `'1HGCM82633A004352'` |
| 4 | `raw_vin="  1HGCM82633A004352  "` | `'1HGCM82633A004352'` |
| 5 | `raw_vin="1M8GDM9AXKP042788"` | `'1M8GDM9AXKP042788'` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Strings, slicing, methods, conditionals, and exceptions.

### Rules and Constraints
- Accept only a string.
- Do not use external VIN services.
- Raise `ValueError` for invalid length or characters.

### Hints
1. Remove spaces and hyphens before checking length.
2. Convert to uppercase once.
3. Validate against the permitted character set.

### Common Mistakes
- Counting separators toward the length.
- Allowing `I`, `O`, or `Q`.
- Returning the original casing.

### Extension Challenge
Format a normalized VIN as groups of 3, 6, and 8 characters for a printed label.
