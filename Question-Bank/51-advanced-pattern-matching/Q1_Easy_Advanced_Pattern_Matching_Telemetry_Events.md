---
layout: default
---

# 51_AdvancedPatternMatching_TelemetryEvents

**Difficulty:** Easy  
**Primary Python Concept:** Structural pattern matching  
**Supporting Concepts:** Mapping patterns, guards, validation  
**Automotive Domain:** Offline telemetry event classification  
**Estimated Completion Time:** 40 minutes

## Learning Objective
Classify event dictionaries with mapping patterns and guarded numeric values.

## Prerequisites
Dictionaries, `match-case`, functions, and validation.

## Scenario Introduction
A replay tool classifies prerecorded speed and battery events.

## Problem Statement
**Goal:** Classify event dictionaries with mapping patterns and guarded numeric values.

**Specifically:** Implement `classify_event(event: dict[str, object]) -> str`.

## Task to Implement
Match `{"type":"speed", "value": value}` and return `OVERSPEED` above 120 km/h or `SPEED_OK`; match battery values at least 20 percent as `BATTERY_OK`, otherwise `BATTERY_LOW`.

## Input Specification
Event type is `speed` or `battery`; values are numeric and speed is 0 through 300, SOC 0 through 100.

## Output Specification
Return the exact classification string.

## Rules and Constraints
- Use mapping patterns and guards.
- Reject missing or malformed fields with `ValueError`.
- Events are offline.

## Hints
Validate the mapping shape first through match cases, then apply guards.

## Common Mistakes
- Using chained `if` statements instead of matching.
- Treating missing values as zero.
- Using an exclusive SOC boundary accidentally.

## Extension Challenge
Add a nested `location` mapping and classify events by region.
