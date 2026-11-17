# 10_LoopControl_InvalidPackets

**Difficulty:** Medium  
**Primary Python Concept:** `continue` and `break`  
**Supporting Concepts:** Validation, filtering, aggregation, dictionaries  
**Automotive Domain:** Simulated telemetry packet processing  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Skip malformed packets with `continue` and stop processing at an end marker with `break`.

## Prerequisites
Lists, dictionaries, loops, conditionals, functions, and exceptions.

## Scenario Introduction
A simulated telemetry stream contains packets with `type` and `value`. A packet with type `END` ends the stream. Invalid packets are skipped.

## Problem Statement
**Goal:** Skip malformed packets with `continue` and stop processing at an end marker with `break`.

**Specifically:** Sum valid `SPEED` packet values before the first end marker and count skipped packets.

## Task to Implement
Implement `process_packets(packets: list[dict[str, object]]) -> dict[str, object]`. Return `speed_total_kmh`, `valid_speed_count`, and `skipped_count`.

## Input Specification
Each item should be a dictionary. Valid speed packets have `type="SPEED"` and numeric `value` from 0 through 300. `END` requires no value. Other packet types are invalid and skipped. The stream may contain 0 to 10,000 items.

## Output Specification
Sum valid speeds without rounding and count them. Count malformed or irrelevant packets before `END` as skipped. Ignore all packets after `END`.

## Rules and Constraints
- Use `continue` for skipped packets and `break` for `END`.
- Do not raise for a malformed packet; skip it.
- Do not mutate input.

## Hints
1. Check for `END` before validating ordinary packets.
2. Increment skipped count before `continue`.
3. Validate speed ranges before aggregation.

## Common Mistakes
- Processing data after `END`.
- Raising instead of skipping malformed packets.
- Counting `END` as skipped.

## Extension Challenge
Track valid `TEMPERATURE` packets in a second aggregate.
