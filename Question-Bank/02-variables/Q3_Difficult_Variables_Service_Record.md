# 02 - Service Record - Difficult

## Question Details
- Concept: Variables, naming conventions, and documentation
- Supporting concepts: Dictionaries, validation, calculations, formatted output
- Difficulty: Difficult
- Domain: Vehicle service records
- Learning Objective: Design a well‑documented function that coordinates multiple named values and produces a reliable service‑cost record.

## Scenario
A workshop estimates a service invoice from labor hours, hourly rate, parts cost, environmental fee, and tax rate. This is an offline educational model; it is not connected to a dealership system.

## Function Details
- Function signature: `create_service_record(vehicle_id: str, labor_hours: float, hourly_rate: float, parts_cost: float, environmental_fee: float, tax_rate_percent: float) -> dict[str, object]`
- Behavior / return shape: Calculate subtotal, tax, and total service cost, while returning an auditable breakdown.
- Exact accepted inputs: `vehicle_id`: non‑empty string (whitespace should be trimmed); `labor_hours`: float in the range **0 – 100** (inclusive); `hourly_rate`, `parts_cost`, `environmental_fee`: float in the range **0 – 100 000** (inclusive); `tax_rate_percent`: float in the range **0 – 30** (inclusive).
- Output and validation / behavior: Return a dictionary with keys: ```python { "vehicle_id": str, "labor_cost": float, "subtotal": float, "tax": float, "total": float, "tax_rate_percent": float, } ``` All monetary values are rounded to two decimal places.

## Tasks to Implement
1. Implement `create_service_record` with the exact signature above and validate the inputs against these accepted rules: `vehicle_id`: non‑empty string (whitespace should be trimmed); `labor_hours`: float in the range **0 – 100** (inclusive); `hourly_rate`, `parts_cost`, `environmental_fee`: float in the range **0 – 100 000** (inclusive); `tax_rate_percent`: float in the range **0 – 30** (inclusive).
2. Calculate subtotal, tax, and total service cost, while returning an auditable breakdown.
3. Implement this output contract exactly: Return a dictionary with keys: ```python { "vehicle_id": str, "labor_cost": float, "subtotal": float, "tax": float, "total": float, "tax_rate_percent": float, } ``` All monetary values are rounded to two decimal places.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | create_service_record("CAR-1", 2, 50, 100, 10, 10) | {"vehicle_id": "CAR-1", "labor_cost": 100.0, "subtotal": 210.0, "tax": 21.0, "total": 231.0, "tax_rate_percent": 10.0} | Typical valid input. |
| 2 | create_service_record(" CAR-2 ", 0, 0, 0, 0, 0) | {"vehicle_id": "CAR-2", "labor_cost": 0.0, "subtotal": 0.0, "tax": 0.0, "total": 0.0, "tax_rate_percent": 0.0} | Valid boundary or threshold case. |
| 3 | create_service_record("CAR-3", 100, 100000, 100000, 100000, 30) | {"vehicle_id": "CAR-3", "labor_cost": 10000000.0, "subtotal": 10200000.0, "tax": 3060000.0, "total": 13260000.0, "tax_rate_percent": 30.0} | Checks an alternate accepted value or input shape. |
| 4 | create_service_record("CAR-4", 1.5, 80, 20, 5, 5) | {"vehicle_id": "CAR-4", "labor_cost": 120.0, "subtotal": 145.0, "tax": 7.25, "total": 152.25, "tax_rate_percent": 5.0} | Checks a second valid boundary or aggregation case. |
| 5 | create_service_record("CAR-5", 0.25, 120, 0, 2.5, 7.5) | {"vehicle_id": "CAR-5", "labor_cost": 30.0, "subtotal": 32.5, "tax": 2.44, "total": 34.94, "tax_rate_percent": 7.5} | Checks another valid input without changing the contract. |

## Expected Deliverables
- Complete implementation of create_service_record that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Variables, functions, dictionaries, arithmetic, conditionals, and exceptions.
