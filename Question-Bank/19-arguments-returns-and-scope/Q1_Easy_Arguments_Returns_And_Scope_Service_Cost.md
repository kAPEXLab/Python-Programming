# 19 - Arguments Returns and Scope Service Cost - Easy

## Question Details
- **Concept:** Arguments, return values, and local scope
- **Supporting Python concepts:** Arithmetic, defaults, validation, rounding
- **Difficulty:** Easy
- **Domain:** Offline service cost estimate
- **Learning Objective:** Use arguments and a local calculation to return a deterministic service estimate.
- **Estimated completion time:** 25 minutes

## Scenario
A workshop simulation charges labor and parts for one service visit.

## Function Details
Implement `service_cost(labor_hours: float, hourly_rate: float, parts_cost: float, tax_rate: float = 0.08) -> dict[str, float]`.

**Required API / operation:** Calculate subtotal, tax, and total without relying on global mutable state.

**Input rules and constraints:** Hours are 0.0 through 100.0, rate and parts cost are 0.0 through 100000.0, and tax rate is 0.0 through 0.30. Values are finite non-booleans.

**Behavior and return shape:** Return `subtotal`, `tax`, and `total`, each rounded to two decimals. Tax is subtotal times tax rate.

**Implementation rules:** Keep intermediate values local to the function. Do not modify arguments or use globals. Raise `ValueError` for invalid values.

## Tasks to Implement
1. Use arguments and a local calculation to return a deterministic service estimate.
2. Calculate subtotal, tax, and total without relying on global mutable state.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `labor_hours=0, hourly_rate=100, parts_cost=0 (default tax)` | `{'subtotal': 0.0, 'tax': 0.0, 'total': 0.0}` |
| 2 | `labor_hours=1, hourly_rate=100, parts_cost=50, tax_rate=0` | `{'subtotal': 150.0, 'tax': 0.0, 'total': 150.0}` |
| 3 | `labor_hours=2, hourly_rate=50, parts_cost=25 (default tax)` | `{'subtotal': 125.0, 'tax': 10.0, 'total': 135.0}` |
| 4 | `labor_hours=1.5, hourly_rate=80, parts_cost=20, tax_rate=0.1` | `{'subtotal': 140.0, 'tax': 14.0, 'total': 154.0}` |
| 5 | `labor_hours=100, hourly_rate=100000, parts_cost=100000, tax_rate=0.3` | `{'subtotal': 10100000.0, 'tax': 3030000.0, 'total': 13130000.0}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Function definitions, parameters, arithmetic, and exceptions.

### Rules and Constraints
- Keep intermediate values local to the function.
- Do not modify arguments or use globals.
- Raise `ValueError` for invalid values.

### Hints
1. Calculate labor before adding parts.
2. Compute tax from subtotal.
3. Round each reported field at the end.

### Common Mistakes
- Applying tax only to parts.
- Reusing a module-level accumulator.
- Rounding inputs before multiplication.

### Extension Challenge
Return a separate rounded labor subtotal and parts subtotal.
