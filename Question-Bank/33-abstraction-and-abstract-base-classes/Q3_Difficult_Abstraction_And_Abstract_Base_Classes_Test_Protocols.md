# 33_AbstractionAndAbstractBaseClasses_TestProtocols

**Difficulty:** Difficult
**Primary Python Concept:** Abstract base classes  
**Supporting Concepts:** Protocol design, result objects, validation, sequencing  
**Automotive Domain:** Offline vehicle test protocols  
**Estimated Completion Time:** 65 minutes

## Learning Objective
Design abstract test protocols that share execution orchestration while specializing their checks.

## Prerequisites
ABC syntax, inheritance, dictionaries, loops, and boolean logic.

## Scenario Introduction
A simulated quality harness runs braking and charging checks against a fixed observation record.

## Problem Statement
**Goal:** Design abstract test protocols that share execution orchestration while specializing their checks.

**Specifically:** Define abstract `TestProtocol` with `name` and `evaluate(observation: dict[str, float]) -> bool`. Implement `BrakeProtocol` requiring `brake_pressure_bar >= 30`, and `ChargeProtocol` requiring `charge_current_a <= 32`.

## Task to Implement
Implement `run_protocols(protocols: list[TestProtocol], observation: dict[str, float]) -> list[tuple[str, bool]]`, preserving protocol order. Missing required fields must raise `KeyError`.

## Input Specification
Protocols must be non-empty. Brake pressure and charge current are finite numbers when present.

## Output Specification
Return `(protocol.name, passed)` pairs. A failed condition returns `False`, not an exception.

## Rules and Constraints
- `evaluate` must be abstract.
- Validate numeric observations before evaluation.
- Use Python 3.12+ and no real test equipment.

## Hints
Keep orchestration generic and let each protocol own its required field.

## Common Mistakes
- Returning only booleans and losing protocol names.
- Treating failed checks as errors.
- Hiding missing fields with defaults.

## Extension Challenge
Add a tire-pressure protocol with four required wheel fields.
