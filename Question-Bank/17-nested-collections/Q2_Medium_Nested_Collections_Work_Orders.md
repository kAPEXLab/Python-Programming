# 17_NestedCollections_WorkOrders

**Difficulty:** Medium  
**Primary Python Concept:** Nested dictionaries and lists  
**Supporting Concepts:** Grouping, validation, sorting, aggregation  
**Automotive Domain:** Simulated workshop work orders  
**Estimated Completion Time:** 40 minutes

## Learning Objective
Group nested work-order items by vehicle and calculate labor totals.

## Prerequisites
Nested collections, dictionaries, loops, arithmetic, and functions.

## Scenario Introduction
Each offline work order names a vehicle and contains line items with hours and hourly rates.

## Problem Statement
**Goal:** Group nested work-order items by vehicle and calculate labor totals.

**Specifically:** Produce per-vehicle labor hours and costs in deterministic order.

## Task to Implement
Implement `summarize_work_orders(orders: list[dict[str, object]]) -> dict[str, dict[str, float]]`.

## Input Specification
Each order has unique `order_id`, non-empty `vehicle_id`, and `items`. Each item has positive finite `hours` up to 100 and `rate` from 1.0 through 500.0. Values are measured to two decimals.

## Output Specification
Return a dictionary keyed by vehicle ID with `hours` and `cost`; cost is rounded to two decimals. Preserve no order requirement for dictionary keys.

## Rules and Constraints
- Sum item hours and `hours * rate` for each vehicle.
- Reject malformed or duplicate order IDs with `ValueError`.
- Do not mutate input.

## Hints
1. Create an accumulator per vehicle.
2. Add hours and cost independently.
3. Round cost after all items for a vehicle are processed.

## Common Mistakes
- Grouping by order instead of vehicle.
- Rounding each line item before summing.
- Accepting negative or zero labor hours.

## Extension Challenge
Return the highest-cost vehicle and its total as a separate field.
