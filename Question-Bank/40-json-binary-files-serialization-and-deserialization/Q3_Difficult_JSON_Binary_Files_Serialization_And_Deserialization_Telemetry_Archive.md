# 40_JSONBinaryFilesSerializationAndDeserialization_TelemetryArchive

**Difficulty:** Difficult
**Primary Python Concept:** JSON, binary files, serialization, and deserialization  
**Supporting Concepts:** Versioned schemas, timestamps, bytes, file paths  
**Automotive Domain:** Offline telemetry archive  
**Estimated Completion Time:** 70 minutes

## Learning Objective
Implement a versioned telemetry archive that can be stored as JSON or binary bytes.

## Prerequisites
JSON, `datetime`, dictionaries, paths, and exception handling.

## Scenario Introduction
A simulator saves timestamped sensor samples for deterministic replay.

## Problem Statement
**Goal:** Implement a versioned telemetry archive that can be stored as JSON or binary bytes.

**Specifically:** Implement `save_archive(path: Path, archive: dict[str, object]) -> None` and `load_archive(path: Path) -> dict[str, object]`.

## Task to Implement
Require `version` equal to 1, `vehicle_id` string, and `samples` list of records with ISO `timestamp` and finite numeric `value`. JSON files are text; `.bin` files contain UTF-8 JSON bytes.

## Input Specification
Vehicle IDs are non-empty. Samples may be empty. Timestamps use `YYYY-MM-DDTHH:MM:SS` without timezone.

## Output Specification
Return the validated archive, preserving sample order and original ISO timestamps.

## Rules and Constraints
- Use `Path`, JSON, and UTF-8 explicitly.
- Validate timestamps with `datetime.fromisoformat`.
- Raise `ValueError` for unsupported version or malformed samples.

## Hints
Keep serialization format selection separate from archive validation.

## Common Mistakes
- Accepting future schema versions.
- Parsing timestamps with ad hoc string slicing.
- Treating binary content as Python repr text.

## Extension Challenge
Add a migration function for version 0 archives.
