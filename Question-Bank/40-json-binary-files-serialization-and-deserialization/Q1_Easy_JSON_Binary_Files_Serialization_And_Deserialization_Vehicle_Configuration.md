# 40 - Saving Vehicle Configuration Snapshots - Easy

## Question Details
- **Concept:** JSON, binary files, serialization, and deserialization
- **Supporting Python concepts:** `pathlib`, JSON schema validation, bytes, deterministic encoding
- **Difficulty:** Easy
- **Domain:** Offline vehicle configuration archive
- **Learning Objective:** Serialize a validated vehicle configuration to JSON and a compact binary payload, then restore it.

## Scenario
A simulator stores configuration snapshots locally for repeatable test runs.

## Function Details
- **Required Python interface:** Implement `save_configuration(path: Path, config: dict[str, object]) -> None` and `load_configuration(path: Path) -> dict[str, object]`.
- **Behavior:** Require `vehicle_id` string, `model_year` integer, and `features` list of strings. Write UTF-8 JSON with sorted keys and a trailing newline; read either `.json` or `.bin`, where binary content is the UTF-8 JSON bytes.
- **Return shape:** Return the validated configuration dictionary with the same values and list order.
- **Input rules and constraints:** IDs are non-empty; model years are 1886 through 2100; feature names are non-empty. Additional constraints: Use `json.dumps(..., sort_keys=True)` and UTF-8 encoding; Use `Path` suffix to select JSON or binary mode; Raise `ValueError` for invalid schema and `FileNotFoundError` for absent files.

## Tasks to Implement
1. Implement the specified Python interface: Implement `save_configuration(path: Path, config: dict[str, object]) -> None` and `load_configuration(path: Path) -> dict[str, object]`.
2. Apply the stated input validation and constraints: IDs are non-empty; model years are 1886 through 2100; feature names are non-empty.
3. Implement the required behavior: Require `vehicle_id` string, `model_year` integer, and `features` list of strings. Write UTF-8 JSON with sorted keys and a trailing newline; read either `.json` or `.bin`, where binary content is the UTF-8 JSON bytes.
4. Return the specified result shape without changing the required ordering or formatting: Return the validated configuration dictionary with the same values and list order.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `save_configuration(Path("config.json"), {"vehicle_id": "EV-1", "model_year": 2026, "features": ["abs", "adas"]}); load_configuration(Path("config.json"))` | `{"features": ["abs", "adas"], "model_year": 2026, "vehicle_id": "EV-1"}; JSON text: {"features": ["abs", "adas"], "model_year": 2026, "vehicle_id": "EV-1"} followed by newline` |
| 2 | `save_configuration(Path("config.bin"), {"vehicle_id": "EV-2", "model_year": 2024, "features": []}); load_configuration(Path("config.bin"))` | `{"features": [], "model_year": 2024, "vehicle_id": "EV-2"}` |
| 3 | `save_configuration(Path("config.json"), {"vehicle_id": "EV-3", "model_year": 1886, "features": ["basic"]}); load_configuration(Path("config.json"))` | `{"features": ["basic"], "model_year": 1886, "vehicle_id": "EV-3"}` |
| 4 | `save_configuration(Path("config.bin"), {"vehicle_id": "EV-4", "model_year": 2100, "features": ["eco"]}); load_configuration(Path("config.bin"))` | `{"features": ["eco"], "model_year": 2100, "vehicle_id": "EV-4"}` |
| 5 | `save_configuration(Path("config.json"), {"vehicle_id": "EV-5", "model_year": 2025, "features": ["comfort", "safety"]}); load_configuration(Path("config.json"))` | `{"features": ["comfort", "safety"], "model_year": 2025, "vehicle_id": "EV-5"}` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Dictionaries, JSON, bytes, file paths, and exception handling.

### Rules and Constraints

- Use `json.dumps(..., sort_keys=True)` and UTF-8 encoding.
- Use `Path` suffix to select JSON or binary mode.
- Raise `ValueError` for invalid schema and `FileNotFoundError` for absent files.

### Hints

Validate the object before serialization and validate decoded data after deserialization.

### Common Mistakes

- Using `str(dict)` instead of JSON.
- Writing text through binary mode without encoding.
- Accepting unknown schema shapes.

### Extension Challenge

Add a schema version field and reject unsupported versions.
