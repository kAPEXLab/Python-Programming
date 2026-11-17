# 25_DataValidation_WarrantyClaim

**Difficulty:** Difficult
**Primary Python Concept:** Data validation  
**Supporting Concepts:** Dates, identifiers, conditional requirements  
**Automotive Domain:** Offline warranty claim intake  
**Estimated Completion Time:** 50 minutes

## Learning Objective
Validate identifiers and conditional claim fields with clear error behavior.

## Prerequisites
Dictionaries, strings, regular expressions, dates, and exceptions.

## Scenario Introduction
A service simulator accepts a warranty claim for a vehicle component and defect category.

## Problem Statement
**Goal:** Validate identifiers and conditional claim fields with clear error behavior.

**Specifically:** Return a normalized claim record that meets the intake schema.

## Task to Implement
Implement `validate_warranty_claim(claim: dict[str, object]) -> dict[str, str]`.

## Input Specification
Required fields: `vin` (17 valid VIN characters), `part_number` (2-12 uppercase letters, digits, or hyphens), `failure_date` (`YYYY-MM-DD`), and `category` (`SAFETY`, `PERFORMANCE`, or `COSMETIC`). `description` is required and non-empty for `SAFETY` claims.

## Output Specification
Return all fields as trimmed strings, with VIN, part number, and category uppercase. Raise `ValueError` on invalid data.

## Rules and Constraints
- Reject extra keys.
- Verify that the date is a real calendar date.
- Do not contact a warranty system or infer eligibility.

## Hints
1. Validate the VIN character set separately.
2. Parse the date with `datetime.date.fromisoformat`.
3. Apply the description rule after normalizing category.

## Common Mistakes
- Accepting impossible dates.
- Requiring descriptions for every category.
- Changing description case unexpectedly.

## Extension Challenge
Add a purchase date and reject claims submitted before purchase.
