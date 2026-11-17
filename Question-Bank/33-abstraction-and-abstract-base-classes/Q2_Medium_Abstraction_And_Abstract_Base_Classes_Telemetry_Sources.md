---
layout: default
---

# 33_AbstractionAndAbstractBaseClasses_TelemetrySources

**Difficulty:** Medium
**Primary Python Concept:** Abstract base classes and interfaces  
**Supporting Concepts:** Iterables, data validation, polymorphism, type hints  
**Automotive Domain:** Offline telemetry source aggregation  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Use an abstract source interface to aggregate normalized telemetry from different simulated sources.

## Prerequisites
Abstract classes, lists, dictionaries, loops, and exceptions.

## Scenario Introduction
A test harness combines battery and cabin telemetry from interchangeable offline sources.

## Problem Statement
**Goal:** Use an abstract source interface to aggregate normalized telemetry from different simulated sources.

**Specifically:** Define abstract `TelemetrySource` with `read() -> dict[str, float]`. Implement `BatterySource` and `CabinSource`, initialized with a dictionary of values.

## Task to Implement
Implement `merge_sources(sources: list[TelemetrySource]) -> dict[str, float]`. Each source must return finite numeric values. Later sources overwrite duplicate keys. Return keys in sorted order when displayed, but preserve a normal dictionary.

## Input Specification
At least one source is required. `BatterySource` supports `soc_percent`; `CabinSource` supports `temperature_c` and `soc_percent`. Values must be finite numbers, and source mappings may contain only keys supported by their source.

## Output Specification
Return one merged dictionary containing all source values.

## Rules and Constraints
- `TelemetrySource` cannot be instantiated directly.
- Read each source exactly once.
- Raise `ValueError` for an empty source list or invalid values.

## Hints
Copy each returned mapping into the aggregate in source order.

## Common Mistakes
- Constructing the abstract source.
- Reading a source multiple times.
- Accepting `nan` as telemetry.

## Extension Challenge
Add a wheel-speed source that emits four named wheel values.
