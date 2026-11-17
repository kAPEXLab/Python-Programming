---
layout: default
---

# 40_JSONBinaryFilesSerializationAndDeserialization_VehicleConfiguration

**Difficulty:** Easy
**Primary Python Concept:** JSON, binary files, serialization, and deserialization  
**Supporting Concepts:** `pathlib`, JSON schema validation, bytes, deterministic encoding  
**Automotive Domain:** Offline vehicle configuration archive  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Serialize a validated vehicle configuration to JSON and a compact binary payload, then restore it.

## Prerequisites
Dictionaries, JSON, bytes, file paths, and exception handling.

## Scenario Introduction
A simulator stores configuration snapshots locally for repeatable test runs.

## Problem Statement
**Goal:** Serialize a validated vehicle configuration to JSON and a compact binary payload, then restore it.

**Specifically:** Implement `save_configuration(path: Path, config: dict[str, object]) -> None` and `load_configuration(path: Path) -> dict[str, object]`.

## Task to Implement
Require `vehicle_id` string, `model_year` integer, and `features` list of strings. Write UTF-8 JSON with sorted keys and a trailing newline; read either `.json` or `.bin`, where binary content is the UTF-8 JSON bytes.

## Input Specification
IDs are non-empty; model years are 1886 through 2100; feature names are non-empty.

## Output Specification
Return the validated configuration dictionary with the same values and list order.

## Rules and Constraints
- Use `json.dumps(..., sort_keys=True)` and UTF-8 encoding.
- Use `Path` suffix to select JSON or binary mode.
- Raise `ValueError` for invalid schema and `FileNotFoundError` for absent files.

## Hints
Validate the object before serialization and validate decoded data after deserialization.

## Common Mistakes
- Using `str(dict)` instead of JSON.
- Writing text through binary mode without encoding.
- Accepting unknown schema shapes.

## Extension Challenge
Add a schema version field and reject unsupported versions.
