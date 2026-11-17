---
layout: default
---

# 01-Python Syntax: ECU Startup Sequence

## Problem Statement
**Your goal:** Implement a function named build_startup_report that validates the input values and returns a single multi-line string describing the ECU startup outcome.

## Function Signature
build_startup_report(ecu_name: str, firmware_version: str, boot_seconds: float) -> str

## Parameters
- ecu_name: a non-empty string containing the ECU identifier.
- firmware_version: a non-empty string containing the firmware version label.
- boot_seconds: a numeric value representing the startup time in seconds.

## Return Value
Return a string with exactly three lines in this order:
1. ECU: <ecu_name>
2. Firmware: <firmware_version>
3. Status: READY or Status: SLOW_BOOT

## Required Behavior
- Accept only non-empty string values for ecu_name and firmware_version.
- Accept boot_seconds only when it is a real number between 0 and 120 inclusive.
- Set the status to READY when boot_seconds is less than or equal to 10.
- Set the status to SLOW_BOOT when boot_seconds is greater than 10.
- Raise ValueError for any invalid input.
