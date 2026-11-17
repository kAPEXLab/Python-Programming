# 35 - Building a Stable Vehicle Event Timeline - Difficult

## Question Details
- **Concept:** Dataclasses and special methods
- **Supporting Python concepts:** Ordering, normalization, immutable records, timestamps
- **Difficulty:** Difficult
- **Domain:** Offline vehicle event timeline
- **Learning Objective:** Create immutable, orderable event records and produce a stable timeline.

## Scenario
A simulator records charging, inspection, and fault events for later review.

## Function Details
- **Required Python interface:** Define frozen dataclass `VehicleEvent` with `timestamp: datetime`, `vehicle_id: str`, `kind: str`, and `detail: str`. Implement `timeline(events: list[VehicleEvent]) -> list[str]`.
- **Behavior:** Sort by timestamp, then vehicle ID, then kind. Format each event as `YYYY-MM-DD HH:MM ID KIND detail`.
- **Return shape:** Return formatted strings in deterministic order.
- **Input rules and constraints:** IDs, kinds, and details are non-empty strings. Timestamps must be timezone-naive `datetime` values for this exercise. Additional constraints: Make events frozen; Do not mutate the input list; Raise `ValueError` for empty text or timezone-aware timestamps.

## Tasks to Implement
1. Implement the specified Python interface: Define frozen dataclass `VehicleEvent` with `timestamp: datetime`, `vehicle_id: str`, `kind: str`, and `detail: str`. Implement `timeline(events: list[VehicleEvent]) -> list[str]`.
2. Apply the stated input validation and constraints: IDs, kinds, and details are non-empty strings. Timestamps must be timezone-naive `datetime` values for this exercise.
3. Implement the required behavior: Sort by timestamp, then vehicle ID, then kind. Format each event as `YYYY-MM-DD HH:MM ID KIND detail`.
4. Return the specified result shape without changing the required ordering or formatting: Return formatted strings in deterministic order.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `[VehicleEvent(datetime(2024, 5, 1, 9, 0), "EV-1", "FAULT", "P0420")]` | `["2024-05-01 09:00 EV-1 FAULT P0420"]` |
| 2 | `[VehicleEvent(datetime(2024, 5, 1, 10, 0), "EV-2", "CHARGE", "done"), VehicleEvent(datetime(2024, 5, 1, 9, 0), "EV-1", "CHECK", "ok")]` | `["2024-05-01 09:00 EV-1 CHECK ok", "2024-05-01 10:00 EV-2 CHARGE done"]` |
| 3 | `[VehicleEvent(datetime(2024, 1, 1, 8, 0), "EV-B", "FAULT", "x"), VehicleEvent(datetime(2024, 1, 1, 8, 0), "EV-A", "FAULT", "y")]` | `["2024-01-01 08:00 EV-A FAULT y", "2024-01-01 08:00 EV-B FAULT x"]` |
| 4 | `[]` | `[]` |
| 5 | `[VehicleEvent(datetime(2025, 12, 31, 23, 59), "EV-1", "Z", "last"), VehicleEvent(datetime(2025, 1, 1, 0, 0), "EV-1", "A", "first")]` | `["2025-01-01 00:00 EV-1 A first", "2025-12-31 23:59 EV-1 Z last"]` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Dataclasses, `datetime`, sorting, strings, and validation.

### Rules and Constraints

- Make events frozen.
- Do not mutate the input list.
- Raise `ValueError` for empty text or timezone-aware timestamps.

### Hints

Use `sorted` with a tuple key and format timestamps with `strftime`.

### Common Mistakes

- Sorting by input order.
- Allowing timezone ambiguity.
- Mutating frozen events.

### Extension Challenge

Add event severity and sort it after timestamp.
