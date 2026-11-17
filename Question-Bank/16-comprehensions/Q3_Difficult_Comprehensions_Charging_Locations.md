---
layout: default
---

# 16_Comprehensions_ChargingLocations

**Difficulty:** Difficult  
**Primary Python Concept:** Nested comprehensions  
**Supporting Concepts:** Nested dictionaries, filtering, sorting, validation  
**Automotive Domain:** Simulated charging location catalog  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Use nested comprehensions to flatten and filter charging connector data.

## Prerequisites
Comprehensions, nested collections, dictionaries, strings, sorting, and validation.

## Scenario Introduction
An offline catalog groups charging connectors by location and connector type.

## Problem Statement
**Goal:** Use nested comprehensions to flatten and filter charging connector data.

**Specifically:** Return sorted locations that offer a requested connector with at least one operational port.

## Task to Implement
Implement `available_charging_locations(locations: dict[str, list[dict[str, object]]], connector: str) -> list[str]`.

## Input Specification
Location names are non-empty strings. Each connector record has `type` (`AC` or `DC`), `ports` (integer 0 through 20), and `operational` (boolean). The requested connector is `AC` or `DC`, case-insensitive.

## Output Specification
Return location names sorted alphabetically where at least one matching connector has `ports > 0` and `operational is True`.

## Rules and Constraints
- Use a comprehension to inspect nested connector records.
- Use a separate filtering step or comprehension for the final list.
- Raise `ValueError` for malformed data; do not mutate input.

## Hints
1. Normalize the requested connector once.
2. Validate every nested record before filtering.
3. Require all three availability conditions in the predicate.

## Common Mistakes
- Treating non-operational ports as usable.
- Returning locations in dictionary insertion order.
- Matching `AC` against every connector type.

## Extension Challenge
Return `(location, connector_type, ports)` tuples for each matching connector.
