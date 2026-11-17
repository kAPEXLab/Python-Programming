---
layout: default
---

# 34_CompositionAndAggregation_VehicleMonitor

**Difficulty:** Easy
**Primary Python Concept:** Composition and aggregation  
**Supporting Concepts:** Object ownership, delegation, validation, type hints  
**Automotive Domain:** Offline vehicle monitor  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Compose a monitor from sensor objects and delegate collection without exposing implementation details.

## Prerequisites
Classes, constructors, methods, lists, and exceptions.

## Scenario Introduction
A simulated vehicle monitor owns a set of sensor objects and produces a snapshot for a test harness.

## Problem Statement
**Goal:** Compose a monitor from sensor objects and delegate collection without exposing implementation details.

**Specifically:** Implement `Sensor(name: str, reading: float)` with `value() -> float`, where `value()` returns the stored reading, then implement `VehicleMonitor(sensors: list[Sensor])` with `snapshot() -> dict[str, float]`.

## Task to Implement
The monitor must aggregate each sensor once, reject duplicate names, and return values keyed by sensor name.

## Input Specification
Sensor names are non-empty and unique. Values must be finite numbers. The sensor list may be empty.

## Output Specification
Return a dictionary snapshot preserving sensor insertion order.

## Rules and Constraints
- The monitor owns the list supplied at construction by making a defensive copy.
- Do not hard-code sensor names.
- Raise `ValueError` for duplicate names or invalid values.

## Hints
Validate sensors while constructing the monitor, then delegate in `snapshot`.

## Common Mistakes
- Retaining a mutable caller list.
- Reading a sensor more than once.
- Silently overwriting duplicate names.

## Extension Challenge
Add a timestamp provider that labels each snapshot.
