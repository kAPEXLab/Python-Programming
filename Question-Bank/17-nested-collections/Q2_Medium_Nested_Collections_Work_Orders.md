# 17 - Work Orders - Medium

## Question Details
- Concept: Nested dictionaries and lists
- Supporting concepts: Grouping, validation, sorting, aggregation
- Difficulty: Medium
- Domain: Simulated workshop work orders
- Learning Objective: Group nested work-order items by vehicle and calculate labor totals.

## Scenario
Each offline work order names a vehicle and contains line items with hours and hourly rates.

## Function Details
- Function signature: `summarize_work_orders(orders: list[dict[str, object]]) -> dict[str, dict[str, float]]`
- Behavior / return shape: Produce per-vehicle labor hours and costs in deterministic order.
- Exact accepted inputs: Each order has unique `order_id`, non-empty `vehicle_id`, and `items`. Each item has positive finite `hours` up to 100 and `rate` from 1.0 through 500.0. Values are measured to two decimals.
- Output and validation / behavior: Return a dictionary keyed by vehicle ID with `hours` and `cost`; cost is rounded to two decimals. Preserve no order requirement for dictionary keys.

## Tasks to Implement
1. Implement `summarize_work_orders` with the exact signature above and validate the inputs against these accepted rules: Each order has unique `order_id`, non-empty `vehicle_id`, and `items`. Each item has positive finite `hours` up to 100 and `rate` from 1.0 through 500.0. Values are measured to two decimals.
2. Produce per-vehicle labor hours and costs in deterministic order.
3. Implement this output contract exactly: Return a dictionary keyed by vehicle ID with `hours` and `cost`; cost is rounded to two decimals. Preserve no order requirement for dictionary keys.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | summarize_work_orders([{"order_id": "O1", "vehicle_id": "V1", "items": [{"hours": 1.0, "rate": 100}]}]) | {"V1": {"hours": 1.0, "cost": 100.0}} | Typical valid input. |
| 2 | summarize_work_orders([{"order_id": "O1", "vehicle_id": "V1", "items": [{"hours": 100.0, "rate": 1.0}]}]) | {"V1": {"hours": 100.0, "cost": 100.0}} | Exercises the maximum accepted hours and minimum hourly rate. |
| 3 | summarize_work_orders([{"order_id": "1", "vehicle_id": "V", "items": [{"hours": 2.0, "rate": 50}, {"hours": 1.0, "rate": 100}]}]) | {"V": {"hours": 3.0, "cost": 200.0}} | Checks an empty or alternate shape. |
| 4 | summarize_work_orders([{"order_id": "A", "vehicle_id": "V1", "items": [{"hours": 0.5, "rate": 10}]}, {"order_id": "B", "vehicle_id": "V2", "items": [{"hours": 3.0, "rate": 20}]}]) | {"V1": {"hours": 0.5, "cost": 5.0}, "V2": {"hours": 3.0, "cost": 60.0}} | Checks an aggregation boundary. |
| 5 | summarize_work_orders([{"order_id": "A", "vehicle_id": "V", "items": [{"hours": 1.25, "rate": 80}]}]) | {"V": {"hours": 1.25, "cost": 100.0}} | Checks multiple records. |

## Expected Deliverables
- Complete implementation of summarize_work_orders that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Nested collections, dictionaries, loops, arithmetic, and functions.

### Rules and Constraints
- Sum item hours and hours * rate for each vehicle.
- Reject malformed or duplicate order IDs with ValueError.
- Do not mutate input.

### Hints
1. Create an accumulator per vehicle.
2. Add hours and cost independently.
3. Round cost after all items for a vehicle are processed.

### Common Mistakes
- Grouping by order instead of vehicle.
- Rounding each line item before summing.
- Accepting negative or zero labor hours.

### Extension Challenge
Return the highest-cost vehicle and its total as a separate field.
