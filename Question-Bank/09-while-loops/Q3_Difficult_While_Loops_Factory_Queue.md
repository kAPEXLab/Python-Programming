---
layout: default
---

# 09_WhileLoops_FactoryQueue

**Difficulty:** Difficult  
**Primary Python Concept:** `while` loops for stateful processing  
**Supporting Concepts:** Lists, dictionaries, validation, queue simulation  
**Automotive Domain:** Manufacturing work queue  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Process a simulated factory queue until empty while maintaining state and a complete result summary.

## Prerequisites
Lists, dictionaries, loops, conditionals, functions, and validation.

## Scenario Introduction
A factory station processes jobs in first-in-first-out order. Each job has an ID, processing time in minutes, and result `PASS` or `FAIL`.

## Problem Statement
**Goal:** Process a simulated factory queue until empty while maintaining state and a complete result summary.

**Specifically:** Process every job and report completion order, total time, and failed job IDs.

## Task to Implement
Implement `process_factory_queue(jobs: list[dict[str, object]]) -> dict[str, object]`.

## Input Specification
- 0 to 10,000 jobs.
- Each job has unique non-empty `job_id`, `minutes` from 0 through 480, and result `PASS` or `FAIL`.
- Reject duplicates, missing fields, or malformed values with `ValueError`.

## Output Specification
Return `completed_ids` in queue order, `total_minutes` as a number, and `failed_ids` in queue order. Zero jobs return empty lists and zero minutes.

## Rules and Constraints
- Use a `while` loop that removes or advances through the queue.
- Do not reorder jobs.
- Do not mutate the caller's list.
- Validate all jobs before processing.

## Hints
1. Validate IDs with a set before processing.
2. Use an index or a shallow copy to protect the input list.
3. Advance exactly once per completed job.

## Common Mistakes
- Processing jobs out of order.
- Mutating the caller's list with `pop()`.
- Counting failed time differently from passed time.

## Extension Challenge
Support a `priority` field while still processing FIFO within equal priorities.
