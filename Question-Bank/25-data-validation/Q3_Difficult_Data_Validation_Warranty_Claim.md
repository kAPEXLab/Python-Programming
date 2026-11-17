# 25 - Data Validation Warranty Claim - Difficult

## Question Details
- **Concept:** Data validation
- **Supporting Python concepts:** Dates, identifiers, conditional requirements
- **Difficulty:** Difficult
- **Domain:** Offline warranty claim intake
- **Learning Objective:** Validate identifiers and conditional claim fields with clear error behavior.
- **Estimated completion time:** 50 minutes

## Scenario
A service simulator accepts a warranty claim for a vehicle component and defect category.

## Function Details
Implement `validate_warranty_claim(claim: dict[str, object]) -> dict[str, str]`.

**Required API / operation:** Return a normalized claim record that meets the intake schema.

**Input rules and constraints:** Required fields: `vin` (17 valid VIN characters), `part_number` (2-12 uppercase letters, digits, or hyphens), `failure_date` (`YYYY-MM-DD`), and `category` (`SAFETY`, `PERFORMANCE`, or `COSMETIC`). `description` is required and non-empty for `SAFETY` claims.

**Behavior and return shape:** Return all fields as trimmed strings, with VIN, part number, and category uppercase. Raise `ValueError` on invalid data.

**Implementation rules:** Reject extra keys. Verify that the date is a real calendar date. Do not contact a warranty system or infer eligibility.

## Tasks to Implement
1. Validate identifiers and conditional claim fields with clear error behavior.
2. Return a normalized claim record that meets the intake schema.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `claim={"vin":"1HGCM82633A004352","part_number":"BP-042","failure_date":"2026-08-26","category":"PERFORMANCE"}` | `{'vin': '1HGCM82633A004352', 'part_number': 'BP-042', 'failure_date': '2026-08-26', 'category': 'PERFORMANCE'}` |
| 2 | `claim={"vin":"1HGCM82633A004352","part_number":"AB","failure_date":"2024-02-29","category":"SAFETY","description":"brake defect"}` | `{'vin': '1HGCM82633A004352', 'part_number': 'AB', 'failure_date': '2024-02-29', 'category': 'SAFETY', 'description': 'brake defect'}` |
| 3 | `claim={"vin":"1hgcm82633a004352","part_number":" bp-1 ","failure_date":"2026-01-01","category":"cosmetic"}` | `{'vin': '1HGCM82633A004352', 'part_number': 'BP-1', 'failure_date': '2026-01-01', 'category': 'COSMETIC'}` |
| 4 | `claim={"vin":"1HGCM82633A004352","part_number":"XYZ123","failure_date":"2000-01-01","category":"SAFETY","description":"  loose connection  "}` | `{'vin': '1HGCM82633A004352', 'part_number': 'XYZ123', 'failure_date': '2000-01-01', 'category': 'SAFETY', 'description': 'loose connection'}` |
| 5 | `claim={"vin":"1HGCM82633A004352","part_number":"AB-2","failure_date":"2025-12-31","category":"PERFORMANCE","description":"reduced output"}` | `{'vin': '1HGCM82633A004352', 'part_number': 'AB-2', 'failure_date': '2025-12-31', 'category': 'PERFORMANCE', 'description': 'reduced output'}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Dictionaries, strings, regular expressions, dates, and exceptions.

### Rules and Constraints
- Reject extra keys.
- Verify that the date is a real calendar date.
- Do not contact a warranty system or infer eligibility.

### Hints
1. Validate the VIN character set separately.
2. Parse the date with `datetime.date.fromisoformat`.
3. Apply the description rule after normalizing category.

### Common Mistakes
- Accepting impossible dates.
- Requiring descriptions for every category.
- Changing description case unexpectedly.

### Extension Challenge
Add a purchase date and reject claims submitted before purchase.
