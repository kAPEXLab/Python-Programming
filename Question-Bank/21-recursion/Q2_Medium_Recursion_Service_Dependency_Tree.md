# 21_Recursion_ServiceDependencyTree

**Difficulty:** Medium  
**Primary Python Concept:** Recursive tree search  
**Supporting Concepts:** Lists, path tracking, validation, early results  
**Automotive Domain:** Offline service dependency tree  
**Estimated Completion Time:** 40 minutes

## Learning Objective
Recursively find the first named service and return its path from the root.

## Prerequisites
Recursion, nested dictionaries, strings, lists, and exceptions.

## Scenario Introduction
A service plan models prerequisite jobs as a tree, with each node containing `service` and `dependencies`.

## Problem Statement
**Goal:** Recursively find the first named service and return its path from the root.

**Specifically:** Find a requested service and report the dependency path used to reach it.

## Task to Implement
Implement `find_service_path(root: dict[str, object], target: str) -> list[str] | None`.

## Input Specification
Service names are non-empty strings; target is non-empty. Each node has a `service` and a list of dependency nodes. Names are unique along any path and maximum depth is 100.

## Output Specification
Return the root-to-target service names as a list, or `None` if target is absent. Matching is case-insensitive after trimming; returned names preserve normalized title case.

## Rules and Constraints
- Use recursion to inspect dependencies.
- Stop searching a branch after finding a match.
- Raise `ValueError` for malformed trees or target; do not mutate input.

## Hints
1. Put the current normalized service on the path.
2. Return immediately when it matches the target.
3. Copy the path when descending so sibling branches stay independent.

## Common Mistakes
- Returning only the target name.
- Sharing one mutable path across sibling branches.
- Continuing after a match.

## Extension Challenge
Return every matching path when duplicate service names are permitted.
