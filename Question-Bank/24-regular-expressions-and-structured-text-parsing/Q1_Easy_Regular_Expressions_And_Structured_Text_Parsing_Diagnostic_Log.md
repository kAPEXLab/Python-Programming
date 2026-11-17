# 24_RegularExpressionsAndStructuredTextParsing_DiagnosticLog

**Difficulty:** Easy
**Primary Python Concept:** Regular expressions and structured text parsing  
**Supporting Concepts:** Named groups, validation, dictionaries  
**Automotive Domain:** Offline diagnostic log parsing  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Parse a strict structured log line with named regular-expression groups.

## Prerequisites
Functions, dictionaries, regular expressions, and exceptions.

## Scenario Introduction
A test harness stores diagnostic events as lines such as `2026-08-26T14:05:07Z|P0420|WARNING|catalyst`.

## Problem Statement
**Goal:** Parse a strict structured log line with named regular-expression groups.

**Specifically:** Extract the timestamp, code, severity, and message from one valid line.

## Task to Implement
Implement `parse_diagnostic_log(line: str) -> dict[str, str]`.

## Input Specification
The exact format is `YYYY-MM-DDTHH:MM:SSZ|CODE|SEVERITY|MESSAGE`. Code is 2 to 8 uppercase letters, digits, or hyphens. Severity is `INFO`, `WARNING`, or `CRITICAL`; message is non-empty and contains no pipe.

## Output Specification
Return keys `timestamp`, `code`, `severity`, and `message` with the captured text unchanged except for no surrounding whitespace.

## Rules and Constraints
- Use `re.fullmatch` or an equivalent anchored pattern.
- Raise `ValueError` for any malformed line.
- Treat the text as offline sample data.

## Hints
1. Capture each field with named groups.
2. Anchor the entire expression with `fullmatch`.
3. Make the message pattern reject the pipe character.

## Common Mistakes
- Using `search` and accepting trailing garbage.
- Making the message optional.
- Splitting on every pipe without validating the schema.

## Extension Challenge
Parse a batch of lines and return only events with `CRITICAL` severity.
