# 28 - Classes and Objects Service Order - Difficult

## Question Details
- **Concept:** Classes and objects
- **Supporting Python concepts:** Lists, state transitions, totals
- **Difficulty:** Difficult
- **Domain:** Offline service-order tracking
- **Learning Objective:** Use an object to hold service items and calculate an order total.
- **Estimated completion time:** 55 minutes

## Scenario
A workshop simulator records labor and parts lines in a service order.

## Function Details
Implement class `ServiceOrder` with `order_id: str`, method `add_item(self, description: str, amount: float) -> None`, and method `subtotal(self) -> float`.

**Required API / operation:** Create an order that accepts line items and reports its subtotal.

**Input rules and constraints:** Order ID is non-empty. Description is non-empty. Amount is finite and non-negative.

**Behavior and return shape:** `subtotal()` returns the sum of item amounts rounded to two decimals. `add_item` returns `None`.

**Implementation rules:** Preserve insertion order internally. Reject invalid inputs with `ValueError`. Do not apply tax or contact a workshop system.

## Tasks to Implement
1. Use an object to hold service items and calculate an order total.
2. Create an order that accepts line items and reports its subtotal.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `order=ServiceOrder("WO-1"); order.subtotal()` | `0.0` |
| 2 | `order=ServiceOrder("WO-2"); order.add_item("Labor", 100); order.subtotal()` | `100.0` |
| 3 | `order=ServiceOrder("WO-3"); order.add_item("Labor", 10.25); order.add_item("Part", 2.5); order.subtotal()` | `12.75` |
| 4 | `order=ServiceOrder("WO-4"); order.add_item("Zero", 0); order.subtotal()` | `0.0` |
| 5 | `order=ServiceOrder("WO-5"); order.add_item("A", 0.1); order.add_item("B", 0.2); order.subtotal()` | `0.3` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, lists, loops, strings, and numeric validation.

### Rules and Constraints
- Preserve insertion order internally.
- Reject invalid inputs with `ValueError`.
- Do not apply tax or contact a workshop system.

### Hints
1. Initialize an instance list in the constructor.
2. Append validated amounts in `add_item`.
3. Sum the list in `subtotal`.

### Common Mistakes
- Resetting items on every addition.
- Returning an unrounded floating-point artifact.
- Allowing invalid descriptions.

### Extension Challenge
Add a read-only count of line items.
