# 39 - Exporting Inspection Reports - Medium

## Question Details
- **Concept:** Text CSV files and file paths
- **Supporting Python concepts:** `pathlib`, CSV dictionaries, deterministic aggregation, validation
- **Difficulty:** Medium
- **Domain:** Offline inspection report export
- **Learning Objective:** Create a CSV inspection report and calculate a pass count from its records.

## Scenario
A workshop simulator records inspection checks in a local report file.

## Function Details
- **Required Python interface:** Implement `export_inspections(path: Path, rows: list[dict[str, object]]) -> None` and `count_passes(path: Path) -> int`.
- **Behavior:** Use columns `vehicle_id,check,status`. Status must be `PASS` or `FAIL`. Count exact `PASS` rows without changing their order or text.
- **Return shape:** Export returns `None`; count returns an integer.
- **Input rules and constraints:** IDs and checks are non-empty strings. Rows must have all three columns. Additional constraints: Use UTF-8 and `csv.DictWriter`/`DictReader`; Paths must be handled with `pathlib.Path`; Raise `ValueError` for missing fields or unknown status.

## Tasks to Implement
1. Implement the specified Python interface: Implement `export_inspections(path: Path, rows: list[dict[str, object]]) -> None` and `count_passes(path: Path) -> int`.
2. Apply the stated input validation and constraints: IDs and checks are non-empty strings. Rows must have all three columns.
3. Implement the required behavior: Use columns `vehicle_id,check,status`. Status must be `PASS` or `FAIL`. Count exact `PASS` rows without changing their order or text.
4. Return the specified result shape without changing the required ordering or formatting: Export returns `None`; count returns an integer.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `export_inspections(Path("checks.csv"), [{"vehicle_id": "EV-1", "check": "brakes", "status": "PASS"}]); count_passes(Path("checks.csv"))` | `1; CSV row: "EV-1,brakes,PASS"` |
| 2 | `export_inspections(Path("checks.csv"), []); count_passes(Path("checks.csv"))` | `0; file contains header "vehicle_id,check,status"` |
| 3 | `export_inspections(Path("checks.csv"), [{"vehicle_id": "EV-2", "check": "lights", "status": "FAIL"}]); count_passes(Path("checks.csv"))` | `0` |
| 4 | `export_inspections(Path("checks.csv"), [{"vehicle_id": "EV-3", "check": "tires", "status": "PASS"}, {"vehicle_id": "EV-3", "check": "horn", "status": "PASS"}]); count_passes(Path("checks.csv"))` | `2` |
| 5 | `export_inspections(Path("checks.csv"), [{"vehicle_id": "EV-4", "check": "battery", "status": "FAIL"}, {"vehicle_id": "EV-4", "check": "cable", "status": "PASS"}]); count_passes(Path("checks.csv"))` | `1` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

CSV, file paths, dictionaries, loops, and numeric conversion.

### Rules and Constraints

- Use UTF-8 and `csv.DictWriter`/`DictReader`.
- Paths must be handled with `pathlib.Path`.
- Raise `ValueError` for missing fields or unknown status.

### Hints

Validate rows before opening the output file so failed input cannot create a partial report.

### Common Mistakes

- Counting case-insensitive statuses.
- Writing a partial file before validation.
- Using string concatenation for CSV.

### Extension Challenge

Add a function that returns failed check names by vehicle.
