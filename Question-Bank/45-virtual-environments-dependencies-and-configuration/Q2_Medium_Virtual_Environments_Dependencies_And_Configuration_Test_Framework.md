# 45_VirtualEnvironmentsDependenciesAndConfiguration_TestFramework

**Difficulty:** Medium  
**Primary Python Concept:** Dependency pinning and environment configuration  
**Supporting Concepts:** `importlib.metadata`, semantic version checks, virtual environments  
**Automotive Domain:** Offline test framework setup  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Verify that an installed test dependency satisfies a deterministic minimum version.

## Prerequisites
Functions, exceptions, package metadata, version strings, and virtual environments.

## Scenario Introduction
A simulated test framework refuses to run when its required local dependency is too old.

## Problem Statement
**Goal:** Verify that an installed test dependency satisfies a deterministic minimum version.

**Specifically:** Implement `require_version(package: str, minimum: tuple[int, int]) -> str` using `importlib.metadata.version`.

## Task to Implement
Parse the package's major and minor version, return `READY:<package>:<version>` when sufficient, and raise `RuntimeError` when missing or too old.

## Input Specification
`package` is a non-empty distribution name; test doubles may provide versions like `2.4.1`.

## Output Specification
Return the exact readiness string for a satisfied dependency.

## Rules and Constraints
- Do not install packages from code.
- Treat missing metadata as a framework error.
- Compare major and minor components numerically.

## Hints
Patch or inject metadata lookup in tests rather than requiring a real installation.

## Common Mistakes
- Comparing version strings lexicographically.
- Installing packages as a side effect.
- Ignoring missing package metadata.

## Extension Challenge
Support a maximum compatible major version from configuration.
