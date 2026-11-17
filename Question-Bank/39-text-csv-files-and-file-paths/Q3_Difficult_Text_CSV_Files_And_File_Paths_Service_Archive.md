# 39 - Filtering a Service Archive - Difficult

## Question Details
- **Concept:** Text CSV files and file paths
- **Supporting Python concepts:** CSV schema validation, `pathlib`, filtering, file errors
- **Difficulty:** Difficult
- **Domain:** Offline service history archive
- **Learning Objective:** Build a validated CSV service archive with selective record loading.

## Scenario
A local archive stores service visits that can be queried by vehicle ID.

## Function Details
- **Required Python interface:** Implement `save_services(path: Path, records: list[dict[str, object]]) -> None` and `load_vehicle_services(path: Path, vehicle_id: str) -> list[dict[str, str]]`.
- **Behavior:** Use columns `vehicle_id,date,odometer_km,operation`. Validate ISO dates, non-negative integer odometers, and non-empty text. Return matching rows in file order.
- **Return shape:** Save returns `None`; load returns matching string-valued rows.
- **Input rules and constraints:** Vehicle ID and operation are non-empty. Dates use `YYYY-MM-DD`; odometer is an integer from 0 upward. Additional constraints: Validate all records before writing; Use only local paths and UTF-8 CSV; Raise `ValueError` for malformed records and `FileNotFoundError` for absent archives.

## Tasks to Implement
1. Implement the specified Python interface: Implement `save_services(path: Path, records: list[dict[str, object]]) -> None` and `load_vehicle_services(path: Path, vehicle_id: str) -> list[dict[str, str]]`.
2. Apply the stated input validation and constraints: Vehicle ID and operation are non-empty. Dates use `YYYY-MM-DD`; odometer is an integer from 0 upward.
3. Implement the required behavior: Use columns `vehicle_id,date,odometer_km,operation`. Validate ISO dates, non-negative integer odometers, and non-empty text. Return matching rows in file order.
4. Return the specified result shape without changing the required ordering or formatting: Save returns `None`; load returns matching string-valued rows.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `save_services(Path("services.csv"), [{"vehicle_id": "EV-1", "date": "2024-01-15", "odometer_km": 1000, "operation": "inspection"}]); load_vehicle_services(Path("services.csv"), "EV-1")` | `[{"vehicle_id": "EV-1", "date": "2024-01-15", "odometer_km": "1000", "operation": "inspection"}]` |
| 2 | `save_services(Path("services.csv"), []); load_vehicle_services(Path("services.csv"), "EV-1")` | `[]` |
| 3 | `save_services(Path("services.csv"), [{"vehicle_id": "EV-1", "date": "2024-02-29", "odometer_km": 0, "operation": "check"}, {"vehicle_id": "EV-2", "date": "2024-03-01", "odometer_km": 4, "operation": "repair"}]); load_vehicle_services(Path("services.csv"), "EV-2")` | `[{"vehicle_id": "EV-2", "date": "2024-03-01", "odometer_km": "4", "operation": "repair"}]` |
| 4 | `save_services(Path("services.csv"), [{"vehicle_id": "EV-3", "date": "2025-12-31", "odometer_km": 25000, "operation": "battery test"}]); load_vehicle_services(Path("services.csv"), "EV-3")` | `[{"vehicle_id": "EV-3", "date": "2025-12-31", "odometer_km": "25000", "operation": "battery test"}]` |
| 5 | `save_services(Path("services.csv"), [{"vehicle_id": "EV-4", "date": "2024-06-01", "odometer_km": 120, "operation": "oil, filter"}]); load_vehicle_services(Path("services.csv"), "EV-4")` | `[{"vehicle_id": "EV-4", "date": "2024-06-01", "odometer_km": "120", "operation": "oil, filter"}]` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

CSV readers and writers, paths, dictionaries, filtering, and exceptions.

### Rules and Constraints

- Validate all records before writing.
- Use only local paths and UTF-8 CSV.
- Raise `ValueError` for malformed records and `FileNotFoundError` for absent archives.

### Hints

Use `date.fromisoformat` to validate dates, then write original ISO text.

### Common Mistakes

- Returning rows for every vehicle.
- Validating only the first record.
- Treating file paths as raw string concatenation.

### Extension Challenge

Add a date-range query using inclusive endpoints.
