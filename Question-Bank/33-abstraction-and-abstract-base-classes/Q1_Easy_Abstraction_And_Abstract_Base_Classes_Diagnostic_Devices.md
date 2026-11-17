# 33_AbstractionAndAbstractBaseClasses_DiagnosticDevices

**Difficulty:** Easy
**Primary Python Concept:** Abstract base classes  
**Supporting Concepts:** Inheritance, abstract methods, type hints, validation  
**Automotive Domain:** Offline diagnostic device adapters  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Define an abstract diagnostic contract and implement multiple concrete devices.

## Prerequisites
Classes, inheritance, exceptions, and basic type annotations.

## Scenario Introduction
A workshop simulator accepts diagnostic devices that expose a common scan operation.

## Problem Statement
**Goal:** Define an abstract diagnostic contract and implement multiple concrete devices.

**Specifically:** Define abstract `DiagnosticDevice` with `scan(code: str) -> str`. Implement `OBDReader` and `CANReader`; OBD returns `OBD:<code>` and CAN returns `CAN:<code>`.

## Task to Implement
Implement `run_scan(device: DiagnosticDevice, code: str) -> str`, validating that the code is a non-empty uppercase alphanumeric string.

## Input Specification
Codes have 2 to 8 characters. Whitespace-only, lowercase, or non-string codes are invalid.

## Output Specification
Return the concrete device prefix followed by the code.

## Rules and Constraints
- Mark `scan` abstract and prevent direct construction of the abstract class.
- Raise `ValueError` for invalid codes.
- Simulation only; do not open a vehicle connection.

## Hints
Use `abc.ABC` and `abc.abstractmethod`.

## Common Mistakes
- Leaving the abstract method concrete.
- Accepting lowercase codes silently.
- Mixing validation with device-specific formatting.

## Extension Challenge
Add a `UDSReader` with a `UDS:` prefix.
