# 30 - Class Methods and Static Methods Fault Catalog - Difficult

## Question Details
- **Concept:** Class methods and static methods
- **Supporting Python concepts:** Class state, lookup, immutable-style construction
- **Difficulty:** Difficult
- **Domain:** Offline diagnostic fault catalog
- **Learning Objective:** Use class-level catalog data with a class method constructor and a static code validator.
- **Estimated completion time:** 55 minutes

## Scenario
A simulator maintains a small catalog of known fault descriptions.

## Function Details
Implement class `FaultCatalog` with class attribute `DESCRIPTIONS`, class method `from_code(cls, code: str) -> FaultCatalog`, and static method `valid_code(code: str) -> bool`. Store normalized `code` and `description`.

**Required API / operation:** Create catalog objects from codes while validating code syntax independently.

**Input rules and constraints:** Codes are 2 to 8 uppercase letters, digits, or hyphens. `DESCRIPTIONS` contains `P0420: "Catalyst efficiency low"` and `BMS-01: "Cell imbalance"`.

**Behavior and return shape:** Known codes use their description; unknown valid codes use `Unknown fault`. Invalid codes raise `ValueError`.

**Implementation rules:** `valid_code` returns only a boolean. `from_code` must use `cls` and uppercase normalization. Do not modify `DESCRIPTIONS`.

## Tasks to Implement
1. Use class-level catalog data with a class method constructor and a static code validator.
2. Create catalog objects from codes while validating code syntax independently.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `FaultCatalog.valid_code('P0420')` | `True` |
| 2 | `FaultCatalog.valid_code('BMS-01')` | `True` |
| 3 | `FaultCatalog.from_code('p0420').description` | `'Catalyst efficiency low'` |
| 4 | `FaultCatalog.from_code('BMS-01').description` | `'Cell imbalance'` |
| 5 | `FaultCatalog.from_code('P0001').description` | `'Unknown fault'` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, dictionaries, class methods, static methods, and strings.

### Rules and Constraints
- `valid_code` returns only a boolean.
- `from_code` must use `cls` and uppercase normalization.
- Do not modify `DESCRIPTIONS`.

### Hints
1. Validate before uppercasing or after consistently normalizing.
2. Use `cls.DESCRIPTIONS.get`.
3. Keep syntax validation independent of catalog membership.

### Common Mistakes
- Returning false for every unknown code.
- Mutating the shared catalog during lookup.
- Making the validator an instance method.

### Extension Challenge
Add a class method that returns a sorted list of all known codes.
