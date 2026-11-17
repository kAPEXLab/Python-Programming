---
layout: default
---

# 50_DescriptorsAndMetaclasses_ConfigurationFields

**Difficulty:** Difficult  
**Primary Python Concept:** Descriptor and metaclass cooperation  
**Supporting Concepts:** Field collection, class creation, validation  
**Automotive Domain:** Offline vehicle configuration  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Collect descriptor-defined configuration fields while validating assignments on instances.

## Prerequisites
Descriptors, metaclasses, inheritance, mappings, and exceptions.

## Scenario Introduction
A simulator configuration class declares bounded fields that should be discoverable and validated uniformly.

## Problem Statement
**Goal:** Collect descriptor-defined configuration fields while validating assignments on instances.

**Specifically:** Implement `ConfigField(value_type: type, default: object)` and `ConfigMeta(type)` with `field_names() -> tuple[str, ...]`.

## Task to Implement
Collect fields in declaration order, expose defaults, and reject assignments of the wrong type. `VehicleConfig` declares `speed_limit: int = ConfigField(int, 120)` and `mode: str = ConfigField(str, "normal")`; speed must be from 0 through 300 and mode must be `normal` or `diagnostic`.

## Input Specification
Speed limit is an integer 0 through 300; mode is `normal` or `diagnostic`.

## Output Specification
Instances expose validated attributes; `field_names()` returns `("speed_limit", "mode")`.

## Rules and Constraints
- Descriptors store per-instance values.
- Validate speed values in the inclusive range 0 through 300 and mode values as `normal` or `diagnostic`.
- Metaclass collection must include inherited fields.
- Configuration is synthetic and offline.

## Hints
Let `__set_name__` capture field names and have the metaclass inspect descriptor instances.

## Common Mistakes
- Sharing values between configuration instances.
- Collecting fields alphabetically instead of declaration order.
- Validating only during serialization.

## Extension Challenge
Add serialization to a plain dictionary while omitting unset optional fields.
