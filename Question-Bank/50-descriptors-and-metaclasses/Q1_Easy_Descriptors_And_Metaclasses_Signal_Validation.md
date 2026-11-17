---
layout: default
---

# 50_DescriptorsAndMetaclasses_SignalValidation

**Difficulty:** Easy  
**Primary Python Concept:** Data descriptors  
**Supporting Concepts:** `__get__`, `__set__`, validation, private storage  
**Automotive Domain:** Offline signal validation  
**Estimated Completion Time:** 40 minutes

## Learning Objective
Use a descriptor to enforce a numeric signal range consistently across instances.

## Prerequisites
Classes, properties, descriptors, and exceptions.

## Scenario Introduction
A simulated sensor model must reject impossible voltage readings at assignment time.

## Problem Statement
**Goal:** Use a descriptor to enforce a numeric signal range consistently across instances.

**Specifically:** Implement `BoundedSignal(minimum: float, maximum: float)` and `BatterySignal` with `voltage = BoundedSignal(0.0, 20.0)`.

## Task to Implement
Store values per instance and raise `ValueError` for values outside the inclusive range or non-numeric values.

## Input Specification
Voltage is a finite number from 0.0 through 20.0 volts; booleans are rejected even though they are integers in Python.

## Output Specification
Reading the attribute returns the assigned float.

## Rules and Constraints
- Implement descriptor methods rather than repeating property code.
- Require finite numeric values and reject booleans.
- Do not use class-level shared storage for values.
- This is not connected to a battery.

## Hints
Use a private instance attribute derived from the descriptor name.

## Common Mistakes
- Storing one value on the descriptor itself.
- Accepting booleans as measurements.
- Validating only on reads.

## Extension Challenge
Allow an optional unit label in the descriptor's constructor.
