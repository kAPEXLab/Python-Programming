---
layout: default
---

# 21_Recursion_ComponentHierarchy

**Difficulty:** Easy  
**Primary Python Concept:** Recursive traversal  
**Supporting Concepts:** Nested dictionaries, base cases, validation, counting  
**Automotive Domain:** Simulated component hierarchy  
**Estimated Completion Time:** 30 minutes

## Learning Objective
Use recursion to count every node in a nested component hierarchy.

## Prerequisites
Functions, dictionaries, lists, conditionals, and validation.

## Scenario Introduction
An offline vehicle fixture represents components as nodes with a name and child nodes.

## Problem Statement
**Goal:** Use recursion to count every node in a nested component hierarchy.

**Specifically:** Count the current component and every descendant.

## Task to Implement
Implement `count_components(node: dict[str, object]) -> int`.

## Input Specification
Each node has a non-empty string `name` and a `children` list of zero or more valid nodes. Maximum depth is 100.

## Output Specification
Return the total number of nodes, including the root.

## Rules and Constraints
- Use a base case for a node with no children.
- Use recursion for every child node.
- Reject malformed nodes with `ValueError` and do not mutate input.

## Hints
1. Count the current node once.
2. Add recursive counts for each child.
3. Validate before descending.

## Common Mistakes
- Returning zero for a leaf.
- Counting only direct children.
- Forgetting malformed nested nodes.

## Extension Challenge
Return the maximum hierarchy depth as well as the node count.
