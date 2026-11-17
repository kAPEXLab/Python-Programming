---
layout: default
---

# 46_CommandLineArgumentsAndEnvironmentVariables_FleetJob

**Difficulty:** Medium  
**Primary Python Concept:** Subcommands and environment configuration  
**Supporting Concepts:** `argparse`, choices, numeric parsing  
**Automotive Domain:** Offline fleet batch job  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Parse a fleet job command with a bounded batch size and configurable region.

## Prerequisites
Command-line parsing, dictionaries, type conversion, and validation.

## Scenario Introduction
A local batch job selects a fleet region and number of prerecorded records.

## Problem Statement
**Goal:** Parse a fleet job command with a bounded batch size and configurable region.

**Specifically:** Implement `parse_job_args(argv: list[str], environ: Mapping[str, str]) -> dict[str, object]`.

## Task to Implement
Parse positional `region` from `north` or `south` and optional `--limit`; default limit comes from `FLEET_JOB_LIMIT` or 100. Return `{"region": ..., "limit": ...}`.

## Input Specification
Limit is an integer from 1 through 1000.

## Output Specification
Return the validated dictionary.

## Rules and Constraints
- CLI `--limit` takes precedence over the environment.
- Translate `argparse` parse errors, including unknown or malformed arguments, into `ValueError`.
- Use `argparse` choices for regions.
- Operate on prerecorded fleet data only.

## Hints
Use `type=int` for the option, then apply environment fallback only when the option is absent.

## Common Mistakes
- Parsing all values as strings.
- Applying defaults before checking CLI values.
- Accepting unsupported regions.

## Extension Challenge
Add a `--dry-run` flag that returns a boolean.
