# 39 - Reading and Writing Fleet Trip CSV - Easy

## Question Details
- **Concept:** Text CSV files and file paths
- **Supporting Python concepts:** `pathlib`, `csv`, validation, context managers
- **Difficulty:** Easy
- **Domain:** Offline fleet trip archive
- **Learning Objective:** Read and write deterministic CSV trip records using safe local paths.

## Scenario
A simulator exports fleet trips for later analysis without contacting a vehicle or service.

## Function Details
- **Required Python interface:** Implement `write_trips(path: Path, trips: list[dict[str, object]]) -> None` and `read_trips(path: Path) -> list[dict[str, str]]`.
- **Behavior:** Write header `vehicle_id,distance_km,energy_kwh` and rows in input order. Read the same header and return string-valued dictionaries.
- **Return shape:** Writing returns `None`; reading returns rows in file order.
- **Input rules and constraints:** IDs are non-empty; distances and energy are non-negative finite numbers. Paths are local filesystem paths. Additional constraints: Use `pathlib.Path` and `csv`, not manual comma joins; Use UTF-8 text and newline handling suitable for CSV; Raise `ValueError` for invalid trip records and `FileNotFoundError` for absent files.

## Tasks to Implement
1. Implement the specified Python interface: Implement `write_trips(path: Path, trips: list[dict[str, object]]) -> None` and `read_trips(path: Path) -> list[dict[str, str]]`.
2. Apply the stated input validation and constraints: IDs are non-empty; distances and energy are non-negative finite numbers. Paths are local filesystem paths.
3. Implement the required behavior: Write header `vehicle_id,distance_km,energy_kwh` and rows in input order. Read the same header and return string-valued dictionaries.
4. Return the specified result shape without changing the required ordering or formatting: Writing returns `None`; reading returns rows in file order.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `write_trips(Path("trips.csv"), [{"vehicle_id": "EV-1", "distance_km": 12.5, "energy_kwh": 3.2}]); read_trips(Path("trips.csv"))` | `[{"vehicle_id": "EV-1", "distance_km": "12.5", "energy_kwh": "3.2"}]` |
| 2 | `write_trips(Path("trips.csv"), []); read_trips(Path("trips.csv"))` | `[]; file contains "vehicle_id,distance_km,energy_kwh\n"` |
| 3 | `read_trips(Path("trips.csv")) for file "vehicle_id,distance_km,energy_kwh\nEV-2,0.0,0.0\n"` | `[{"vehicle_id": "EV-2", "distance_km": "0.0", "energy_kwh": "0.0"}]` |
| 4 | `write_trips(Path("trips.csv"), [{"vehicle_id": "EV,3", "distance_km": 100.0, "energy_kwh": 20.0}]); read_trips(Path("trips.csv"))` | `[{"vehicle_id": "EV,3", "distance_km": "100.0", "energy_kwh": "20.0"}]` |
| 5 | `write_trips(Path("trips.csv"), [{"vehicle_id": "EV-5", "distance_km": 0.0, "energy_kwh": 1.25}]); read_trips(Path("trips.csv"))` | `[{"vehicle_id": "EV-5", "distance_km": "0.0", "energy_kwh": "1.25"}]` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Functions, lists, dictionaries, `pathlib`, and CSV basics.

### Rules and Constraints

- Use `pathlib.Path` and `csv`, not manual comma joins.
- Use UTF-8 text and newline handling suitable for CSV.
- Raise `ValueError` for invalid trip records and `FileNotFoundError` for absent files.

### Hints

Let `csv.DictWriter` and `csv.DictReader` manage quoting and headers.

### Common Mistakes

- Splitting lines on commas manually.
- Omitting the header.
- Converting values during a function specified to return strings.

### Extension Challenge

Add a `started_at` ISO date column.
