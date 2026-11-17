# 32_InheritancePolymorphismAndOverriding_SensorReaders

**Difficulty:** Medium
**Primary Python Concept:** Inheritance, polymorphism, and method overriding  
**Supporting Concepts:** Class design, numeric validation, formatting, type hints  
**Automotive Domain:** Offline sensor reader normalization  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Build interchangeable sensor readers whose overridden methods normalize different raw units.

## Prerequisites
Classes, inheritance, methods, exceptions, and floating-point arithmetic.

## Scenario Introduction
A test bench receives raw values from temperature, pressure, and speed sensors. Each reader must expose the same interface while applying its own conversion.

## Problem Statement
**Goal:** Build interchangeable sensor readers whose overridden methods normalize different raw units.

**Specifically:** Create `SensorReader` with `read(raw_value: float) -> float`, then implement `TemperatureReader`, `PressureReader`, and `SpeedReader`. Add `read_all(readers: list[SensorReader], values: list[float]) -> list[float]`.

## Task to Implement
Temperature converts Celsius to Fahrenheit using `c * 9 / 5 + 32`; pressure converts kPa to psi using `kpa * 0.1450377`; speed converts km/h to m/s using `kmh / 3.6`. Round each result to two decimal places.

## Input Specification
Both lists must have equal nonzero length. Raw values must be finite numbers. Temperature is in Celsius, pressure in kPa, and speed in km/h.

## Output Specification
Return normalized values in reader order, rounded to two decimal places.

## Rules and Constraints
- `read_all` must call `read` polymorphically.
- Raise `ValueError` for invalid list lengths or non-finite values.
- No hardware, network, or external packages.

## Hints
Validate shared input requirements before dispatching to reader methods.

## Common Mistakes
- Applying one conversion to every reader.
- Rounding before conversion.
- Matching readers by class name.

## Extension Challenge
Add a voltage reader that converts millivolts to volts.
