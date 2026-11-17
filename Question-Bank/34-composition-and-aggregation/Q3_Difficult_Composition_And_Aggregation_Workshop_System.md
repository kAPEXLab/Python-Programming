---
layout: default
---

# 34_CompositionAndAggregation_WorkshopSystem

**Difficulty:** Difficult
**Primary Python Concept:** Composition and aggregation  
**Supporting Concepts:** Delegation, nested objects, state transitions, exceptions  
**Automotive Domain:** Offline workshop workflow  
**Estimated Completion Time:** 65 minutes

## Learning Objective
Compose work orders from service tasks while aggregating their duration and status.

## Prerequisites
Classes, composition, lists, validation, and string formatting.

## Scenario Introduction
A simulated workshop system owns tasks inside each work order and reports readiness for completion.

## Problem Statement
**Goal:** Compose work orders from service tasks while aggregating their duration and status.

**Specifically:** Implement `ServiceTask(code: str, minutes: int, complete: bool = False)` and `WorkOrder(order_id: str, tasks: list[ServiceTask])`. Add `WorkshopSystem(orders: list[WorkOrder])` with `ready_orders() -> list[str]`.

## Task to Implement
A work order is ready only when it has at least one task and every task is complete. `ready_orders` returns order IDs sorted ascending.

## Input Specification
Task codes are non-empty; minutes are integers from 1 through 600. `complete` must be an actual `bool`, not an integer or another truthy value. Order IDs are unique and non-empty.

## Output Specification
Return ready order IDs only. Duplicate task codes within an order are invalid.

## Rules and Constraints
- `WorkOrder` owns a defensive copy of its task list.
- `WorkshopSystem` aggregates order objects without modifying them.
- Raise `ValueError` for invalid records.

## Hints
Let `WorkOrder` answer whether it is ready; the system should delegate to it.

## Common Mistakes
- Marking an empty order ready because `all([])` is true.
- Sorting by insertion order only.
- Sharing the caller's mutable task list.

## Extension Challenge
Add total minutes for all open orders.
