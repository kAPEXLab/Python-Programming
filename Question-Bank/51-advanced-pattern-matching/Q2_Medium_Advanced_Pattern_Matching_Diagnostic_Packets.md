---
layout: default
---

# 51_AdvancedPatternMatching_DiagnosticPackets

**Difficulty:** Medium  
**Primary Python Concept:** Nested class and sequence patterns  
**Supporting Concepts:** Dataclasses, guards, packet validation  
**Automotive Domain:** Offline diagnostic packets  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Use class and sequence patterns to classify typed diagnostic packet records.

## Prerequisites
Dataclasses, tuples, `match-case`, and exception handling.

## Scenario Introduction
A local analyzer receives synthetic packets represented by dataclasses and payload tuples.

## Problem Statement
**Goal:** Use class and sequence patterns to classify typed diagnostic packet records.

**Specifically:** Define `DiagnosticPacket(kind: str, payload: tuple[object, ...])` and implement `classify_packet(packet: DiagnosticPacket) -> str`.

## Task to Implement
Classify `"fault"` with one string code as `FAULT:<code>`, `"reading"` with one numeric value at least 0 as `READING`, and reject other shapes.

## Input Specification
Packets use the stated dataclass and supported payload shapes.

## Output Specification
Return the exact classification or raise `ValueError` for invalid packets.

## Rules and Constraints
- Use class and sequence patterns.
- Do not mutate packet payloads.
- No real diagnostic bus is involved.

## Hints
Match the dataclass fields directly and nest tuple patterns in each case.

## Common Mistakes
- Accepting payloads with extra values.
- Matching only on `kind` and skipping payload validation.
- Converting all payloads to strings.

## Extension Challenge
Add a sequence packet that accepts exactly three numeric samples.
