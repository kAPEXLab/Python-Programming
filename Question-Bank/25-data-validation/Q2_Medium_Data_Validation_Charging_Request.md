# 25 - Data Validation Charging Request - Medium

## Question Details
- **Concept:** Data validation
- **Supporting Python concepts:** Cross-field rules, literals, numeric constraints
- **Difficulty:** Medium
- **Domain:** Offline charging request validation
- **Learning Objective:** Apply both field-level and cross-field validation to a charging request.
- **Estimated completion time:** 45 minutes

## Scenario
A charging planner receives a requested current, target state of charge, and connector type.

## Function Details
Implement `validate_charging_request(request: dict[str, object]) -> dict[str, object]`.

**Required API / operation:** Normalize a request only if its values are safe for the simulated connector.

**Input rules and constraints:** Keys are `connector` (`AC` or `DC`), `current_a` (1-500), and `target_soc` (1-100). DC current may be up to 500 A; AC current may be up to 80 A. Values are finite numbers where applicable.

**Behavior and return shape:** Return `{"connector": uppercase, "current_a": float, "target_soc": float}`. Raise `ValueError` for invalid keys, types, ranges, or connector limits.

**Implementation rules:** Reject extra keys. Target SOC must be greater than 0 and at most 100. This is a planning validation function, not a charger controller.

## Tasks to Implement
1. Apply both field-level and cross-field validation to a charging request.
2. Normalize a request only if its values are safe for the simulated connector.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `request={'connector': 'AC', 'current_a': 1, 'target_soc': 1}` | `{'connector': 'AC', 'current_a': 1.0, 'target_soc': 1.0}` |
| 2 | `request={'connector': 'ac', 'current_a': 80, 'target_soc': 100}` | `{'connector': 'AC', 'current_a': 80.0, 'target_soc': 100.0}` |
| 3 | `request={'connector': 'DC', 'current_a': 500, 'target_soc': 80}` | `{'connector': 'DC', 'current_a': 500.0, 'target_soc': 80.0}` |
| 4 | `request={'connector': 'dc', 'current_a': 32.5, 'target_soc': 50.5}` | `{'connector': 'DC', 'current_a': 32.5, 'target_soc': 50.5}` |
| 5 | `request={'connector': 'AC', 'current_a': 32, 'target_soc': 75}` | `{'connector': 'AC', 'current_a': 32.0, 'target_soc': 75.0}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Dictionaries, conditionals, type checks, and exceptions.

### Rules and Constraints
- Reject extra keys.
- Target SOC must be greater than 0 and at most 100.
- This is a planning validation function, not a charger controller.

### Hints
1. Normalize the connector before cross-field checks.
2. Use a connector-to-limit mapping.
3. Validate the key set before reading values.

### Common Mistakes
- Applying the same current limit to AC and DC.
- Allowing target SOC above 100.
- Returning the caller's mutable dictionary.

### Extension Challenge
Add battery chemistry with separate maximum SOC values.
