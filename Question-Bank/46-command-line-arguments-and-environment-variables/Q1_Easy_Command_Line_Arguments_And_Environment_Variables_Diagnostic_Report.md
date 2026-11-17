---
layout: default
---

# 46_CommandLineArgumentsAndEnvironmentVariables_DiagnosticReport

**Difficulty:** Easy  
**Primary Python Concept:** `argparse` and environment variables  
**Supporting Concepts:** Defaults, parsing, required values  
**Automotive Domain:** Offline diagnostic report  
**Estimated Completion Time:** 35 minutes

## Learning Objective
Parse a report vehicle ID from command-line arguments with an environment fallback.

## Prerequisites
Functions, lists, `argparse`, and mappings.

## Scenario Introduction
A local diagnostic script needs a vehicle identifier without contacting a vehicle.

## Problem Statement
**Goal:** Parse a report vehicle ID from command-line arguments with an environment fallback.

**Specifically:** Implement `parse_report_args(argv: list[str], environ: Mapping[str, str]) -> str`.

## Task to Implement
Accept optional `--vehicle-id`; if absent use `DIAGNOSTIC_VEHICLE_ID`. Return the identifier or raise `ValueError` when missing or blank.

## Input Specification
Arguments are shell-like strings; the environment mapping contains optional text values.

## Output Specification
Return the stripped vehicle identifier.

## Rules and Constraints
- Use `argparse`; do not manually index `argv`.
- Translate `argparse` parse errors, including unknown or malformed arguments, into `ValueError`.
- Explicit command-line input wins over the environment.
- No live diagnostic access is needed.

## Hints
Use `parser.parse_args(argv)` and inspect the parsed namespace.

## Common Mistakes
- Reading `sys.argv` inside the function.
- Treating whitespace as an identifier.
- Allowing environment values to override CLI values.

## Extension Challenge
Add `--format` with `text` and `json` choices.
