# 40 - Persisting Versioned Telemetry Archives - Difficult

## Question Details
- **Concept:** JSON, binary files, serialization, and deserialization
- **Supporting Python concepts:** Versioned schemas, timestamps, bytes, file paths
- **Difficulty:** Difficult
- **Domain:** Offline telemetry archive
- **Learning Objective:** Implement a versioned telemetry archive that can be stored as JSON or binary bytes.

## Scenario
A simulator saves timestamped sensor samples for deterministic replay.

## Function Details
- **Required Python interface:** Implement `save_archive(path: Path, archive: dict[str, object]) -> None` and `load_archive(path: Path) -> dict[str, object]`.
- **Behavior:** Require `version` equal to 1, `vehicle_id` string, and `samples` list of records with ISO `timestamp` and finite numeric `value`. JSON files are text; `.bin` files contain UTF-8 JSON bytes.
- **Return shape:** Return the validated archive, preserving sample order and original ISO timestamps.
- **Input rules and constraints:** Vehicle IDs are non-empty. Samples may be empty. Timestamps use `YYYY-MM-DDTHH:MM:SS` without timezone. Additional constraints: Use `Path`, JSON, and UTF-8 explicitly; Validate timestamps with `datetime.fromisoformat`; Raise `ValueError` for unsupported version or malformed samples.

## Tasks to Implement
1. Implement the specified Python interface: Implement `save_archive(path: Path, archive: dict[str, object]) -> None` and `load_archive(path: Path) -> dict[str, object]`.
2. Apply the stated input validation and constraints: Vehicle IDs are non-empty. Samples may be empty. Timestamps use `YYYY-MM-DDTHH:MM:SS` without timezone.
3. Implement the required behavior: Require `version` equal to 1, `vehicle_id` string, and `samples` list of records with ISO `timestamp` and finite numeric `value`. JSON files are text; `.bin` files contain UTF-8 JSON bytes.
4. Return the specified result shape without changing the required ordering or formatting: Return the validated archive, preserving sample order and original ISO timestamps.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `save_archive(Path("archive.json"), {"version": 1, "vehicle_id": "EV-1", "samples": []}); load_archive(Path("archive.json"))` | `{"version": 1, "vehicle_id": "EV-1", "samples": []}` |
| 2 | `save_archive(Path("archive.bin"), {"version": 1, "vehicle_id": "EV-2", "samples": [{"timestamp": "2024-01-01T00:00:00", "value": 12.5}]}); load_archive(Path("archive.bin"))` | `{"version": 1, "vehicle_id": "EV-2", "samples": [{"timestamp": "2024-01-01T00:00:00", "value": 12.5}]}` |
| 3 | `save_archive(Path("archive.json"), {"version": 1, "vehicle_id": "EV-3", "samples": [{"timestamp": "2024-02-29T23:59:59", "value": 0}]}); load_archive(Path("archive.json"))` | `{"version": 1, "vehicle_id": "EV-3", "samples": [{"timestamp": "2024-02-29T23:59:59", "value": 0}]}` |
| 4 | `save_archive(Path("archive.bin"), {"version": 1, "vehicle_id": "EV-4", "samples": [{"timestamp": "2025-12-31T12:30:00", "value": 99.125}]}); load_archive(Path("archive.bin"))` | `{"version": 1, "vehicle_id": "EV-4", "samples": [{"timestamp": "2025-12-31T12:30:00", "value": 99.125}]}` |
| 5 | `save_archive(Path("archive.json"), {"version": 1, "vehicle_id": "EV-5", "samples": [{"timestamp": "2024-05-01T08:00:00", "value": -1.5}, {"timestamp": "2024-05-01T08:01:00", "value": 2.5}]}); load_archive(Path("archive.json"))` | `{"version": 1, "vehicle_id": "EV-5", "samples": [{"timestamp": "2024-05-01T08:00:00", "value": -1.5}, {"timestamp": "2024-05-01T08:01:00", "value": 2.5}]}` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

JSON, `datetime`, dictionaries, paths, and exception handling.

### Rules and Constraints

- Use `Path`, JSON, and UTF-8 explicitly.
- Validate timestamps with `datetime.fromisoformat`.
- Raise `ValueError` for unsupported version or malformed samples.

### Hints

Keep serialization format selection separate from archive validation.

### Common Mistakes

- Accepting future schema versions.
- Parsing timestamps with ad hoc string slicing.
- Treating binary content as Python repr text.

### Extension Challenge

Add a migration function for version 0 archives.
