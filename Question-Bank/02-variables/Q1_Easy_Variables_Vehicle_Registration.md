# 02_Variables_VehicleRegistration

**Difficulty:** Easy  
**Primary Python Concept:** Variables and naming conventions  
**Supporting Concepts:** Strings, numeric values, validation, formatted output  
**Automotive Domain:** Vehicle registration  
**Estimated Completion Time:** 20 minutes

## Learning Objective
Store related vehicle information in clearly named variables and produce a readable registration summary.

## Prerequisites
Assignment statements, strings, numbers, `print()`, and basic conditionals.

## Scenario Introduction
A dealership records basic information before a vehicle is delivered. The registration record uses a vehicle identification number (VIN), model year, mileage in km, and fuel type.

## Problem Statement
**Goal:** Store related vehicle information in clearly named variables and produce a readable registration summary.

**Specifically:** Create a validated registration summary for one vehicle.

## Task to Implement
Implement `create_registration(vin: str, model_year: int, mileage_km: int, fuel_type: str) -> str`. Return one line containing all four fields in the specified order.

## Input Specification
- `vin`: exactly 17 uppercase letters or digits.
- `model_year`: integer from 1886 through 2100.
- `mileage_km`: integer from 0 through 2,000,000.
- `fuel_type`: one of `PETROL`, `DIESEL`, `HYBRID`, or `ELECTRIC`.

## Output Specification
Return: `VIN=<vin>; Year=<year>; Mileage=<mileage> km; Fuel=<fuel>`.

## Rules and Constraints
- Use descriptive `snake_case` variable names.
- Reject invalid values with `ValueError`.
- Preserve the uppercase fuel value.
- Do not use global variables.

## Hints
- Correctness: 3 points
- Variable use and naming: 1 point
- Input validation: 1 point
- Edge-case handling: 1 point
- Readability: 1 point
- Modularity: 1 point
- Efficiency: 0.5 point
- Documentation: 0.5 point
- Testability: 1 point

1. Store each parameter in a clearly named local variable if needed.
2. Validate the VIN length and allowed characters.
3. Use an f-string for the final line.

### Hint Rubric
- Validate that `vin` is exactly 17 characters and contains only uppercase letters and digits.
- Ensure `model_year` is between 1886 and 2100 inclusive.
- Ensure `mileage_km` is between 0 and 2_000_000 inclusive.
- Confirm `fuel_type` is one of `PETROL`, `DIESEL`, `HYBRID`, `ELECTRIC`.
- Construct the output string with an f‑string matching the required format.

## Common Mistakes
- Using unclear names such as `x` and `y`.
- Accepting invalid fuel labels.
- Allowing negative mileage.
- Changing the required output punctuation.

## Extension Challenge
Add an optional `owner_id` field with validation while preserving backward compatibility.
