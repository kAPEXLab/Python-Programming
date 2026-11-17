---
layout: default
---

# 47_IterablesIteratorsGeneratorsAndGeneratorExpressions_LargeLogFile

**Difficulty:** Medium  
**Primary Python Concept:** Generator functions  
**Supporting Concepts:** Lazy file iteration, `yield`, filtering  
**Automotive Domain:** Offline large diagnostic log  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Stream matching diagnostic lines without loading a complete log into memory.

## Prerequisites
Generators, strings, file-like objects, and loops.

## Scenario Introduction
A large prerecorded log must expose only lines containing a requested diagnostic code.

## Problem Statement
**Goal:** Stream matching diagnostic lines without loading a complete log into memory.

**Specifically:** Implement `matching_lines(lines: Iterable[str], code: str) -> Iterator[str]`.

## Task to Implement
Yield stripped lines containing the exact case-sensitive `code`, in original order. Reject a blank code.

## Input Specification
`lines` is any iterable of text lines; `code` is a non-empty string.

## Output Specification
Yield matching stripped strings lazily.

## Rules and Constraints
- Use `yield`; do not return a list.
- Preserve duplicate matches and order.
- Input is prerecorded and contains no proprietary data.

## Hints
Strip each line immediately before checking and yielding it.

## Common Mistakes
- Reading all lines into a list first.
- Using substring normalization that changes case behavior.
- Dropping duplicate events.

## Extension Challenge
Yield `(line_number, line)` pairs while remaining lazy.
