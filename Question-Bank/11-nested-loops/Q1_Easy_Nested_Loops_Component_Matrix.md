---
layout: default
---

# 11_NestedLoops_ComponentMatrix

**Difficulty:** Easy  
**Primary Python Concept:** Nested `for` loops  
**Supporting Concepts:** Lists, strings, validation, counting  
**Automotive Domain:** Component inspection matrix  
**Estimated Completion Time:** 25 minutes

## Learning Objective
Use nested loops to inspect every cell in a two-dimensional test matrix.

## Prerequisites
Lists, loops, booleans, functions, and validation.

## Scenario Introduction
A factory checks rows of vehicles against columns of inspection items. Each cell contains `PASS` or `FAIL`.

## Problem Statement
**Goal:** Use nested loops to inspect every cell in a two-dimensional test matrix.

**Specifically:** Count total cells and failed cells in the matrix.

## Task to Implement
Implement `count_matrix_failures(matrix: list[list[str]]) -> dict[str, int]`.

## Input Specification
The matrix has 0 to 100 rows. Each row has 0 to 100 cells, and all rows must have equal length. Cells are case-insensitive `PASS` or `FAIL`. Reject ragged or invalid matrices with `ValueError`.

## Output Specification
Return `total_checks` and `failed_checks`.

## Rules and Constraints
- Use two nested `for` loops.
- An empty matrix returns both counts as zero.
- Do not mutate input.

## Hints
1. Validate row lengths before counting.
2. Outer loop handles rows; inner loop handles cells.
3. Normalize each cell before comparison.

## Common Mistakes
- Checking only the first row.
- Accepting ragged rows.
- Counting lowercase labels as invalid.

## Extension Challenge
Return the zero-based coordinates of every failed cell.
