# 51_AdvancedPatternMatching_UpdateManifest

**Difficulty:** Difficult  
**Primary Python Concept:** Nested mapping patterns with guards  
**Supporting Concepts:** OR patterns, captures, validation, version checks  
**Automotive Domain:** Offline software update manifest  
**Estimated Completion Time:** 60 minutes

## Learning Objective
Validate and route nested update manifests with precise structural pattern matching.

## Prerequisites
Dictionaries, pattern matching, guards, tuples, and validation.

## Scenario Introduction
A simulator checks a synthetic update manifest before reporting whether it is eligible.

## Problem Statement
**Goal:** Validate and route nested update manifests with precise structural pattern matching.

**Specifically:** Implement `evaluate_manifest(manifest: dict[str, object]) -> str`.

## Task to Implement
Match `{"target": {"model": model, "version": version}, "package": package}`. Return `READY:<model>:<version>` when package is `"full"` or `"delta"` and version is a three-integer tuple; a non-empty string package value other than `"full"` or `"delta"` returns `REJECTED_FORMAT`. Non-string or blank package values, and missing or otherwise malformed structure, raise `ValueError`.

## Input Specification
Model and package are non-empty strings; version is `(major, minor, patch)` with non-negative integers.

## Output Specification
Return the exact ready or rejected string.

## Rules and Constraints
- Use nested mapping patterns and an OR pattern for package values.
- Do not download, install, or connect to a vehicle.
- Version tuple length and types must be validated.

## Hints
Use a nested mapping case to capture values, then use a guard for package and version rules.

## Common Mistakes
- Accepting a two-part version.
- Treating `patch` as equivalent to `delta`.
- Mutating the manifest during evaluation.

## Extension Challenge
Add a `compatibility` mapping and require its model to match the target model.
