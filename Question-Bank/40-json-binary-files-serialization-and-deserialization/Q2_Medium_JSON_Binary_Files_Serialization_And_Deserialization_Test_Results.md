# 40 - Serializing Test Results - Medium

## Question Details
- **Concept:** JSON, binary files, serialization, and deserialization
- **Supporting Python concepts:** Nested data, schema validation, bytes, rounding
- **Difficulty:** Medium
- **Domain:** Offline vehicle test-result archive
- **Learning Objective:** Persist nested test results while preserving deterministic numeric and list data.

## Scenario
A quality harness saves simulated test outcomes for later review.

## Function Details
- **Required Python interface:** Implement `serialize_results(results: dict[str, object]) -> bytes` and `deserialize_results(payload: bytes) -> dict[str, object]`.
- **Behavior:** Require `vehicle_id`, `passed` boolean, and `checks` list. Each check has `name` string and `score` number from 0 through 100. Serialize sorted-key JSON as UTF-8 bytes; scores must be rounded to two decimals.
- **Return shape:** Return bytes from serialization and the validated dictionary from deserialization.
- **Input rules and constraints:** The vehicle ID and check names are non-empty. At least one check is required. Additional constraints: Do not use pickle; Reject malformed UTF-8, invalid JSON, and invalid schema with `ValueError`; Preserve check order.

## Tasks to Implement
1. Implement the specified Python interface: Implement `serialize_results(results: dict[str, object]) -> bytes` and `deserialize_results(payload: bytes) -> dict[str, object]`.
2. Apply the stated input validation and constraints: The vehicle ID and check names are non-empty. At least one check is required.
3. Implement the required behavior: Require `vehicle_id`, `passed` boolean, and `checks` list. Each check has `name` string and `score` number from 0 through 100. Serialize sorted-key JSON as UTF-8 bytes; scores must be rounded to two decimals.
4. Return the specified result shape without changing the required ordering or formatting: Return bytes from serialization and the validated dictionary from deserialization.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `serialize_results({"vehicle_id": "EV-1", "passed": True, "checks": [{"name": "brakes", "score": 99.876}]})` | `b'{"checks": [{"name": "brakes", "score": 99.88}], "passed": true, "vehicle_id": "EV-1"}'` |
| 2 | `serialize_results({"vehicle_id": "EV-2", "passed": False, "checks": [{"name": "lights", "score": 0}]})` | `b'{"checks": [{"name": "lights", "score": 0}], "passed": false, "vehicle_id": "EV-2"}'` |
| 3 | `deserialize_results(b'{"vehicle_id": "EV-3", "passed": true, "checks": [{"name": "tires", "score": 100}]}')` | `{"checks": [{"name": "tires", "score": 100}], "passed": true, "vehicle_id": "EV-3"}` |
| 4 | `serialize_results({"vehicle_id": "EV-4", "passed": True, "checks": [{"name": "cable", "score": 75.554}, {"name": "plug", "score": 80.004}]})` | `b'{"checks": [{"name": "cable", "score": 75.55}, {"name": "plug", "score": 80.0}], "passed": true, "vehicle_id": "EV-4"}'` |
| 5 | `deserialize_results(b'{"checks": [{"name": "range", "score": 42.5}], "passed": false, "vehicle_id": "EV-5"}')` | `{"checks": [{"name": "range", "score": 42.5}], "passed": false, "vehicle_id": "EV-5"}` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

JSON, dictionaries, lists, binary file modes, and validation.

### Rules and Constraints

- Do not use pickle.
- Reject malformed UTF-8, invalid JSON, and invalid schema with `ValueError`.
- Preserve check order.

### Hints

Decode bytes explicitly, call `json.loads`, then validate each nested check.

### Common Mistakes

- Using pickle for untrusted data.
- Validating only top-level keys.
- Rounding after serialization instead of before normalization.

### Extension Challenge

Add a binary checksum field and verify it before decoding.
