# 29 - Constructors Attributes and Instance Methods Tire Inspection - Easy

## Question Details
- **Concept:** Constructors, attributes, and instance methods
- **Supporting Python concepts:** Lists, thresholds, formatted status
- **Difficulty:** Easy
- **Domain:** Offline tire inspection
- **Learning Objective:** Design a class whose constructor validates measurements and whose method derives status.
- **Estimated completion time:** 50 minutes

## Scenario
An inspector records tread depth for four tires in millimeters.

## Function Details
Implement class `TireInspection` with constructor `__init__(self, depths_mm: list[float])` and method `status(self) -> str`.

**Required API / operation:** Create a tire inspection object and classify the set as `PASS` or `REPLACE`.

**Input rules and constraints:** Exactly four finite depths are required, each from 0 through 20 mm.

**Behavior and return shape:** Return `REPLACE` if any depth is below 1.6 mm; otherwise return `PASS`.

**Implementation rules:** Copy the input list so outside mutation cannot alter the object. Raise `ValueError` for wrong length or invalid values. The threshold is strictly below 1.6.

## Tasks to Implement
1. Design a class whose constructor validates measurements and whose method derives status.
2. Create a tire inspection object and classify the set as `PASS` or `REPLACE`.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `TireInspection([1.6, 1.6, 1.6, 1.6]).status()` | `'PASS'` |
| 2 | `TireInspection([1.59, 5, 5, 5]).status()` | `'REPLACE'` |
| 3 | `TireInspection([0, 0, 0, 0]).status()` | `'REPLACE'` |
| 4 | `TireInspection([20, 20, 20, 20]).status()` | `'PASS'` |
| 5 | `TireInspection([2.5, 3.1, 1.6, 4]).status()` | `'PASS'` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, constructors, lists, conditionals, and validation.

### Rules and Constraints
- Copy the input list so outside mutation cannot alter the object.
- Raise `ValueError` for wrong length or invalid values.
- The threshold is strictly below 1.6.

### Hints
1. Validate length before iterating values.
2. Store `list(depths_mm)`.
3. Use `any` for the replacement rule.

### Common Mistakes
- Accepting three or five tires.
- Using `<= 1.6` instead of `< 1.6`.
- Keeping the caller's list by reference.

### Extension Challenge
Report the index of every tire below the threshold.
