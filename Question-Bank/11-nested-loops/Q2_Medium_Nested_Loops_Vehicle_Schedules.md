---
layout: default
---

# 11_NestedLoops_VehicleSchedules

**Difficulty:** Medium  
**Primary Python Concept:** Nested loops and pair comparison  
**Supporting Concepts:** Dictionaries, lists, validation, conflict detection  
**Automotive Domain:** Fleet service scheduling  
**Estimated Completion Time:** 40 minutes

## Learning Objective
Compare every pair of scheduled jobs to detect overlapping work for the same vehicle.

## Prerequisites
Nested loops, dictionaries, tuples, conditionals, and validation.

## Scenario Introduction
A fleet workshop schedules jobs using start and end times in minutes from the beginning of a day. Two jobs conflict if they target the same vehicle and their time intervals overlap.

## Problem Statement
**Goal:** Compare every pair of scheduled jobs to detect overlapping work for the same vehicle.

**Specifically:** Return the IDs of all conflicting job pairs in input order.

## Task to Implement
Implement `find_schedule_conflicts(jobs: list[dict[str, object]]) -> list[tuple[str, str]]`. Each job has unique `job_id`, `vehicle_id`, `start_minute`, and `end_minute`.

## Input Specification
There are 0 to 2,000 jobs. Times are integers from 0 through 1,440, and `start_minute < end_minute`. Intervals use half-open semantics: a job ending at 100 does not conflict with one starting at 100.

## Output Specification
Return pairs `(earlier_input_job_id, later_input_job_id)` for conflicts, ordered by first index then second index.

## Rules and Constraints
- Use nested loops to compare pairs.
- Compare only jobs with the same vehicle ID.
- Reject duplicate IDs or malformed jobs with `ValueError`.

## Hints
1. For each pair, compare only when vehicle IDs match.
2. Two half-open intervals overlap when each starts before the other ends.
3. Keep the original pair order.

## Common Mistakes
- Treating touching intervals as overlapping.
- Comparing jobs from different vehicles.
- Returning reversed or sorted pairs.

## Extension Challenge
Return each conflict with its overlap duration in minutes.
