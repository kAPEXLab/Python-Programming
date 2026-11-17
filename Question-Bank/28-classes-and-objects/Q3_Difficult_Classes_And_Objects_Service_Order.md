---
layout: default
---

# 28_ClassesAndObjects_ServiceOrder

**Difficulty:** Difficult
**Primary Python Concept:** Classes and objects  
**Supporting Concepts:** Lists, state transitions, totals  
**Automotive Domain:** Offline service-order tracking  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Use an object to hold service items and calculate an order total.

## Prerequisites
Classes, lists, loops, strings, and numeric validation.

## Scenario Introduction
A workshop simulator records labor and parts lines in a service order.

## Problem Statement
**Goal:** Use an object to hold service items and calculate an order total.

**Specifically:** Create an order that accepts line items and reports its subtotal.

## Task to Implement
Implement class `ServiceOrder` with `order_id: str`, method `add_item(self, description: str, amount: float) -> None`, and method `subtotal(self) -> float`.

## Input Specification
Order ID is non-empty. Description is non-empty. Amount is finite and non-negative.

## Output Specification
`subtotal()` returns the sum of item amounts rounded to two decimals. `add_item` returns `None`.

## Rules and Constraints
- Preserve insertion order internally.
- Reject invalid inputs with `ValueError`.
- Do not apply tax or contact a workshop system.

## Hints
1. Initialize an instance list in the constructor.
2. Append validated amounts in `add_item`.
3. Sum the list in `subtotal`.

## Common Mistakes
- Resetting items on every addition.
- Returning an unrounded floating-point artifact.
- Allowing invalid descriptions.

## Extension Challenge
Add a read-only count of line items.
