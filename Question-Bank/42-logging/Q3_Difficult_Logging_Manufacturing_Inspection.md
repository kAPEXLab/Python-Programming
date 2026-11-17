# 42 - Logging Manufacturing Inspections - Difficult

## Question Details
- **Concept:** Structured logging with contextual fields
- **Supporting Python concepts:** `LoggerAdapter`, exception logging, deterministic records
- **Difficulty:** Difficult
- **Domain:** Offline manufacturing inspection
- **Learning Objective:** Use contextual logging to make inspection outcomes traceable without exposing proprietary information.

## Scenario
A simulated manufacturing station inspects a component and needs the station and part number in every log record.

## Function Details
- **Required Python interface:** Implement `ManufacturingInspection(logger: logging.Logger, station: str)` with `inspect(part_number: str, measured_mm: float) -> str`.
- **Behavior:** Accept measurements from 9.95 through 10.05 mm inclusive, log `INFO`, and return `PASS:<part_number>`. Otherwise log `WARNING` and return `REJECT:<part_number>`. Malformed input raises `ValueError` and logs `ERROR`.
- **Return shape:** Return the exact pass or reject result. Every record must carry `station` and `part_number` context.
- **Input rules and constraints:** `station` and `part_number` are non-empty strings. `measured_mm` is finite and numeric. Additional constraints: Use a logger adapter or an equivalent structured `extra` mapping; Do not log secrets or real manufacturing data; Boundary comparisons are inclusive.

## Tasks to Implement
1. Implement the specified Python interface: Implement `ManufacturingInspection(logger: logging.Logger, station: str)` with `inspect(part_number: str, measured_mm: float) -> str`.
2. Apply the stated input validation and constraints: `station` and `part_number` are non-empty strings. `measured_mm` is finite and numeric.
3. Implement the required behavior: Accept measurements from 9.95 through 10.05 mm inclusive, log `INFO`, and return `PASS:<part_number>`. Otherwise log `WARNING` and return `REJECT:<part_number>`. Malformed input raises `ValueError` and logs `ERROR`.
4. Return the specified result shape without changing the required ordering or formatting: Return the exact pass or reject result. Every record must carry `station` and `part_number` context.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `inspection = ManufacturingInspection(logger, "LINE-1"); inspection.inspect("PART-1", 10.0); capture record` | `("PASS:PART-1", INFO, station="LINE-1", part_number="PART-1")` |
| 2 | `inspection = ManufacturingInspection(logger, "LINE-1"); inspection.inspect("PART-2", 9.95); capture record` | `("PASS:PART-2", INFO, station="LINE-1", part_number="PART-2")` |
| 3 | `inspection = ManufacturingInspection(logger, "LINE-1"); inspection.inspect("PART-3", 10.05); capture record` | `("PASS:PART-3", INFO, station="LINE-1", part_number="PART-3")` |
| 4 | `inspection = ManufacturingInspection(logger, "LINE-1"); inspection.inspect("PART-4", 9.949); capture record` | `("REJECT:PART-4", WARNING, station="LINE-1", part_number="PART-4")` |
| 5 | `inspection = ManufacturingInspection(logger, "LINE-1"); inspection.inspect("PART-5", 10.051); capture record` | `("REJECT:PART-5", WARNING, station="LINE-1", part_number="PART-5")` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Logging, classes, dictionaries, validation, and exception handling.

### Rules and Constraints

- Use a logger adapter or an equivalent structured `extra` mapping.
- Do not log secrets or real manufacturing data.
- Boundary comparisons are inclusive.

### Hints

Build context once, validate types before comparisons, and keep severity tied to the outcome.

### Common Mistakes

- Comparing numeric strings silently.
- Omitting context from error records.
- Treating tolerance endpoints as rejected.

### Extension Challenge

Add a `reason` field to every rejected inspection record.
