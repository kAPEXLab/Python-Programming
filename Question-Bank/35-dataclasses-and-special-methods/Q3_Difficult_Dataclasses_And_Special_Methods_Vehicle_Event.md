---
layout: default
---

# 35_DataclassesAndSpecialMethods_VehicleEvent

**Difficulty:** Difficult
**Primary Python Concept:** Dataclasses and special methods  
**Supporting Concepts:** Ordering, normalization, immutable records, timestamps  
**Automotive Domain:** Offline vehicle event timeline  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Create immutable, orderable event records and produce a stable timeline.

## Prerequisites
Dataclasses, `datetime`, sorting, strings, and validation.

## Scenario Introduction
A simulator records charging, inspection, and fault events for later review.

## Problem Statement
**Goal:** Create immutable, orderable event records and produce a stable timeline.

**Specifically:** Define frozen dataclass `VehicleEvent` with `timestamp: datetime`, `vehicle_id: str`, `kind: str`, and `detail: str`. Implement `timeline(events: list[VehicleEvent]) -> list[str]`.

## Task to Implement
Sort by timestamp, then vehicle ID, then kind. Format each event as `YYYY-MM-DD HH:MM ID KIND detail`.

## Input Specification
IDs, kinds, and details are non-empty strings. Timestamps must be timezone-naive `datetime` values for this exercise.

## Output Specification
Return formatted strings in deterministic order.

## Rules and Constraints
- Make events frozen.
- Do not mutate the input list.
- Raise `ValueError` for empty text or timezone-aware timestamps.

## Hints
Use `sorted` with a tuple key and format timestamps with `strftime`.

## Common Mistakes
- Sorting by input order.
- Allowing timezone ambiguity.
- Mutating frozen events.

## Extension Challenge
Add event severity and sort it after timestamp.
