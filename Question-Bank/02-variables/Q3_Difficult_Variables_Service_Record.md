# 02-Variables: Service Record

**Difficulty:** Difficult  
**Primary Python Concept:** Variables, naming conventions, and documentation  
**Supporting Concepts:** Dictionaries, validation, calculations, formatted output  
**Automotive Domain:** Vehicle service records  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Design a well‑documented function that coordinates multiple named values and produces a reliable service‑cost record.

## Prerequisites
Variables, functions, dictionaries, arithmetic, conditionals, and exceptions.

## Scenario Introduction
A workshop estimates a service invoice from labor hours, hourly rate, parts cost, environmental fee, and tax rate. This is an offline educational model; it is not connected to a dealership system.

## Problem Statement
**Goal:** Design a well‑documented function that coordinates multiple named values and produces a reliable service‑cost record.

**Specifically:** Calculate subtotal, tax, and total service cost, while returning an auditable breakdown.

## Task to Implement
Implement `create_service_record(vehicle_id: str, labor_hours: float, hourly_rate: float, parts_cost: float, environmental_fee: float, tax_rate_percent: float) -> dict[str, object]`.

The function must:
- Return the vehicle ID and five monetary fields: `labor_cost`, `subtotal`, `tax`, `total`, and `tax_rate_percent`.
- Validate inputs and raise `ValueError` for any out‑of‑range or malformed data.
- Perform calculations without premature rounding and round the final monetary values to two decimal places.
- **Do not** print anything; only return the dictionary.

## Input Specification
- `vehicle_id`: non‑empty string (whitespace should be trimmed).
- `labor_hours`: float in the range **0 – 100** (inclusive).
- `hourly_rate`, `parts_cost`, `environmental_fee`: float in the range **0 – 100 000** (inclusive).
- `tax_rate_percent`: float in the range **0 – 30** (inclusive).

## Output Specification
Return a dictionary with keys:
```python
{
    "vehicle_id": str,
    "labor_cost": float,
    "subtotal": float,
    "tax": float,
    "total": float,
    "tax_rate_percent": float,
}
```
All monetary values are rounded to two decimal places.

## Rules & Constraints
- Include a descriptive docstring.
- Use clear `snake_case` variable names.
- Validate every input and raise `ValueError` with an informative message when a constraint is violated.
- Do **not** round intermediate results; only round the final values that appear in the returned dictionary.
- Do **not** print or log inside the function.

## Hint Rubric
- **Validation:** Trim `vehicle_id`; ensure it is non‑empty after stripping. Verify numeric ranges for all other parameters.
- **Labor Cost:** `labor_cost = labor_hours * hourly_rate`.
- **Subtotal:** `subtotal = labor_cost + parts_cost + environmental_fee`.
- **Tax:** `tax = subtotal * (tax_rate_percent / 100)`.
- **Total:** `total = subtotal + tax`.
- **Rounding:** Use `round(value, 2)` on each monetary result before placing it in the dictionary.
- **Return:** Build the dictionary in a stable order and return it.
