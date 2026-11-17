# 30 - Class Methods and Static Methods Unit Conversion - Medium

## Question Details
- **Concept:** Class methods and static methods
- **Supporting Python concepts:** Alternate constructors, conversion formulas, validation
- **Difficulty:** Medium
- **Domain:** Offline measurement conversion utility
- **Learning Objective:** Separate unit-independent conversion logic from class-level construction.
- **Estimated completion time:** 50 minutes

## Scenario
A test report stores speed in km/h but accepts technician input in mph.

## Function Details
Implement class `UnitConversion` with `from_mph(cls, mph: float) -> UnitConversion`, attribute `kmh`, and static method `mph_to_kmh(mph: float) -> float`.

**Required API / operation:** Create a converter object from mph and expose a static conversion helper.

**Input rules and constraints:** Mph is finite and from 0 through 250. Use exact factor `1.609344`.

**Behavior and return shape:** `mph_to_kmh` returns km/h rounded to three decimals. `from_mph` stores that rounded result in `kmh`.

**Implementation rules:** Use `@classmethod` for `from_mph` and `@staticmethod` for the formula. Raise `ValueError` outside the range. No locale-dependent formatting is required.

## Tasks to Implement
1. Separate unit-independent conversion logic from class-level construction.
2. Create a converter object from mph and expose a static conversion helper.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `UnitConversion.mph_to_kmh(0)` | `0.0` |
| 2 | `UnitConversion.mph_to_kmh(1)` | `1.609` |
| 3 | `UnitConversion.mph_to_kmh(60)` | `96.561` |
| 4 | `UnitConversion.from_mph(250).kmh` | `402.336` |
| 5 | `UnitConversion.from_mph(12.5).kmh` | `20.117` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, decorators, arithmetic, and exceptions.

### Rules and Constraints
- Use `@classmethod` for `from_mph` and `@staticmethod` for the formula.
- Raise `ValueError` outside the range.
- No locale-dependent formatting is required.

### Hints
1. Validate in the static method so both paths share it.
2. Multiply by `1.609344`.
3. Call the static method from the class method.

### Common Mistakes
- Using 1.6 and losing required precision.
- Requiring an instance to call the formula.
- Rounding the conversion factor itself.

### Extension Challenge
Add a class method for km/h input that uses a shared range validator.
