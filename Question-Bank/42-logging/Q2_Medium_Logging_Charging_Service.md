---
layout: default
---

# 42_Logging_ChargingService

**Difficulty:** Medium  
**Primary Python Concept:** Logger hierarchy and handlers  
**Supporting Concepts:** `StringIO`, log capture, severity filtering  
**Automotive Domain:** Offline charging service  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Capture charging lifecycle messages with stable levels and a predictable logger configuration.

## Prerequisites
Logging basics, classes, context-free service methods, and string streams.

## Scenario Introduction
An offline charging service reports session start, completion, and rejected requests for a test harness.

## Problem Statement
**Goal:** Capture charging lifecycle messages with stable levels and a predictable logger configuration.

**Specifically:** Implement `ChargingService(logger: logging.Logger)` with `start_session(vehicle_id: str, target_soc: int) -> str`.

## Task to Implement
Log `INFO` for accepted starts, `WARNING` when the target is already reached, and `ERROR` for invalid input. Return `STARTED:<vehicle_id>:<target_soc>%` for accepted requests.

## Input Specification
`vehicle_id` is non-empty. `target_soc` is an integer from 1 through 100. A target below the current fixed simulated SOC of 80 is a warning and returns `ALREADY_REACHED`.

## Output Specification
Return either the exact started string, `ALREADY_REACHED`, or raise `ValueError`.

## Rules and Constraints
- The logger must be named `charging.service` or be supplied by the caller.
- Do not write directly to stdout.
- Data and charging are simulated only.

## Hints
Use one logger call per outcome and attach a temporary handler in tests.

## Common Mistakes
- Treating a warning as an exception.
- Accepting boolean values as SOC integers.
- Printing messages instead of logging them.

## Extension Challenge
Add a session identifier and include it in every log record.
