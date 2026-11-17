# 24_RegularExpressionsAndStructuredTextParsing_CANTextDump

**Difficulty:** Medium
**Primary Python Concept:** Regular expressions and structured text parsing  
**Supporting Concepts:** Repeated records, hexadecimal validation, list results  
**Automotive Domain:** Offline CAN text dump parsing  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Extract repeated hexadecimal CAN frames from structured text.

## Prerequisites
Regular expressions, lists, dictionaries, loops, and validation.

## Scenario Introduction
A simulator exports frames as `ID=7E8 DLC=3 DATA=01 0A FF`, one frame per line.

## Problem Statement
**Goal:** Extract repeated hexadecimal CAN frames from structured text.

**Specifically:** Parse every valid frame in a dump and preserve input order.

## Task to Implement
Implement `parse_can_dump(text: str) -> list[dict[str, object]]`.

## Input Specification
Each non-empty line must contain an uppercase or lowercase hexadecimal ID from 1 to 3 digits, DLC from 0 to 8, and exactly DLC two-digit hexadecimal data bytes separated by spaces.

## Output Specification
Return dictionaries with integer `can_id`, integer `dlc`, and list[int] `data`. Raise `ValueError` if any non-empty line is invalid.

## Rules and Constraints
- Use a regular expression to validate and capture each line.
- `DLC=0` must have an empty data list.
- Do not interpret the input as a live bus connection.

## Hints
1. Process lines with `splitlines`.
2. Capture the data text separately, then split bytes.
3. Compare byte count with the captured DLC.

## Common Mistakes
- Accepting non-hex bytes.
- Returning hexadecimal strings instead of integers.
- Treating blank lines as frames.

## Extension Challenge
Add an optional timestamp prefix while retaining support for the original format.
