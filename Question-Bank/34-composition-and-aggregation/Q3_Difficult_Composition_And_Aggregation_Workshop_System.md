# 34 - Composition and Aggregation Workshop System - Difficult

## Question Details
- **Concept:** Composition and aggregation
- **Supporting Python concepts:** Delegation, nested objects, state transitions, exceptions
- **Difficulty:** Difficult
- **Domain:** Offline workshop workflow
- **Learning Objective:** Compose work orders from service tasks while aggregating their duration and status.
- **Estimated completion time:** 65 minutes

## Scenario
A simulated workshop system owns tasks inside each work order and reports readiness for completion.

## Function Details
A work order is ready only when it has at least one task and every task is complete. `ready_orders` returns order IDs sorted ascending.

**Required API / operation:** Implement `ServiceTask(code: str, minutes: int, complete: bool = False)` and `WorkOrder(order_id: str, tasks: list[ServiceTask])`. Add `WorkshopSystem(orders: list[WorkOrder])` with `ready_orders() -> list[str]`.

**Input rules and constraints:** Task codes are non-empty; minutes are integers from 1 through 600. `complete` must be an actual `bool`, not an integer or another truthy value. Order IDs are unique and non-empty.

**Behavior and return shape:** Return ready order IDs only. Duplicate task codes within an order are invalid.

**Implementation rules:** `WorkOrder` owns a defensive copy of its task list. `WorkshopSystem` aggregates order objects without modifying them. Raise `ValueError` for invalid records.

## Tasks to Implement
1. Compose work orders from service tasks while aggregating their duration and status.
2. Implement `ServiceTask(code: str, minutes: int, complete: bool = False)` and `WorkOrder(order_id: str, tasks: list[ServiceTask])`. Add `WorkshopSystem(orders: list[WorkOrder])` with `ready_orders() -> list[str]`.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `WorkshopSystem([WorkOrder('WO-1', [ServiceTask('A', 10, True)])]).ready_orders()` | `['WO-1']` |
| 2 | `WorkshopSystem([WorkOrder('WO-2', [])]).ready_orders()` | `[]` |
| 3 | `WorkshopSystem([WorkOrder('WO-3', [ServiceTask('A', 10, False)])]).ready_orders()` | `[]` |
| 4 | `WorkshopSystem([WorkOrder('Z', [ServiceTask('A', 1, True)]), WorkOrder('A', [ServiceTask('B', 600, True)])]).ready_orders()` | `['A', 'Z']` |
| 5 | `WorkshopSystem([WorkOrder('WO-4', [ServiceTask('A', 1, True), ServiceTask('B', 600, True)])]).ready_orders()` | `['WO-4']` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, composition, lists, validation, and string formatting.

### Rules and Constraints
- `WorkOrder` owns a defensive copy of its task list.
- `WorkshopSystem` aggregates order objects without modifying them.
- Raise `ValueError` for invalid records.

### Hints
Let `WorkOrder` answer whether it is ready; the system should delegate to it.

### Common Mistakes
- Marking an empty order ready because `all([])` is true.
- Sorting by insertion order only.
- Sharing the caller's mutable task list.

### Extension Challenge
Add total minutes for all open orders.
