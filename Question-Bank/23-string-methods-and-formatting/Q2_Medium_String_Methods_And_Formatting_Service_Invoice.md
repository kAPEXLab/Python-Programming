# 23_StringMethodsAndFormatting_ServiceInvoice

**Difficulty:** Medium
**Primary Python Concept:** String methods and formatting  
**Supporting Concepts:** Numeric formatting, validation, f-strings  
**Automotive Domain:** Offline service invoice text  
**Estimated Completion Time:** 40 minutes

## Learning Objective
Format numeric service data into a stable, human-readable invoice line.

## Prerequisites
Strings, f-strings, floats, arithmetic, and exceptions.

## Scenario Introduction
A workshop simulator needs one deterministic line for a labor item and its parts charge.

## Problem Statement
**Goal:** Format numeric service data into a stable, human-readable invoice line.

**Specifically:** Calculate subtotal and tax, then format the invoice without currency ambiguity.

## Task to Implement
Implement `format_invoice_line(description: str, labor_hours: float, hourly_rate: float, parts_cost: float, tax_rate: float) -> str`.

## Input Specification
Description must be non-empty after trimming. Labor hours, hourly rate, and parts cost are non-negative finite numbers. Tax rate is from 0 through 1 inclusive.

## Output Specification
Return `DESCRIPTION | subtotal=NN.NN | tax=NN.NN | total=NN.NN`, with all amounts rounded to two decimals and no currency symbols.

## Rules and Constraints
- Normalize description by trimming repeated internal whitespace to single spaces.
- Calculate subtotal as labor hours times hourly rate plus parts cost.
- Raise `ValueError` for invalid input.

## Hints
1. Normalize the description with `split` and `join`.
2. Keep calculations numeric until final formatting.
3. Use two decimal places in each formatted amount.

## Common Mistakes
- Applying tax only to labor.
- Rounding subtotal before calculating tax.
- Leaving repeated spaces in the description.

## Extension Challenge
Return a multiline invoice with separate labor and parts lines while preserving exact rounding.
