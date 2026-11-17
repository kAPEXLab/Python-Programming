---
layout: default
---

# 43_ModulesAndPackages_TelemetryReaders

**Difficulty:** Difficult  
**Primary Python Concept:** Package-relative imports  
**Supporting Concepts:** Reader protocols, parsing, package API boundaries  
**Automotive Domain:** Offline telemetry readers  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Combine specialized readers through package-relative imports while preserving a stable public API.

## Prerequisites
Packages, relative imports, functions, protocols, and validation.

## Scenario Introduction
An offline telemetry package reads text samples from battery and tire-pressure sources.

## Problem Statement
**Goal:** Combine specialized readers through package-relative imports while preserving a stable public API.

**Specifically:** Implement `read_sample(source: str, payload: str) -> tuple[str, float]` in a package that delegates to source-specific reader modules.

## Task to Implement
For `battery`, parse a voltage such as `"12.60V"`; for `tire`, parse pressure such as `"2.40bar"`. Return `(source, value)` rounded to two places.

## Input Specification
Source is `battery` or `tire`; payload contains the exact unit suffix and a finite non-negative number.

## Output Specification
Return a tuple like `("battery", 12.6)` or `("tire", 2.4)`.

## Rules and Constraints
- Use relative imports between package modules.
- Reject unknown sources and malformed units with `ValueError`.
- Samples are prerecorded and offline.

## Hints
Keep unit parsing inside each reader and dispatch from one package-level function.

## Common Mistakes
- Accepting a battery payload for the tire reader.
- Using absolute imports that only work from one directory.
- Returning the raw payload.

## Extension Challenge
Add a `temperature` reader for payloads ending in `C`.
