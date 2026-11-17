# 24_RegularExpressionsAndStructuredTextParsing_ManufacturingLabel

**Difficulty:** Difficult
**Primary Python Concept:** Regular expressions and structured text parsing  
**Supporting Concepts:** Optional groups, dates, normalization  
**Automotive Domain:** Offline component manufacturing labels  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Parse a compact label containing required and optional manufacturing fields.

## Prerequisites
Regular expressions, strings, dictionaries, and validation.

## Scenario Introduction
A test fixture receives labels in the form `PART:BP-042;LOT:2026A17;REV:03;DATE:2026-08-26`.

## Problem Statement
**Goal:** Parse a compact label containing required and optional manufacturing fields.

**Specifically:** Extract the four label fields and normalize their values for inventory inspection.

## Task to Implement
Implement `parse_manufacturing_label(label: str) -> dict[str, str]`.

## Input Specification
Fields must appear exactly in the order `PART`, `LOT`, `REV`, `DATE`, separated by semicolons. Part is 2 to 10 uppercase letters, digits, or hyphens; lot is 4 to 12 alphanumeric characters; revision is two digits; date is ISO `YYYY-MM-DD`.

## Output Specification
Return lowercase keys `part`, `lot`, `revision`, and `date`, preserving field values except for trimming surrounding whitespace.

## Rules and Constraints
- Use one anchored regular expression with named groups.
- Reject unknown fields, missing fields, and invalid separators with `ValueError`.
- Date shape must be validated; calendar validity may be checked with `datetime`.

## Hints
1. Escape literal punctuation in the pattern.
2. Use named groups for readable result construction.
3. Anchor both ends of the label.

## Common Mistakes
- Accepting fields in any order.
- Converting revision `00` to integer zero.
- Using a loose search instead of a full match.

## Extension Challenge
Support an optional `COLOR` field only after `DATE`, returning it when present.
