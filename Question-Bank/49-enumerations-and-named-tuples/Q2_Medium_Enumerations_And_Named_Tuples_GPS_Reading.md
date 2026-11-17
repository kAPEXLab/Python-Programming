# 49 - Creating Immutable GPS Readings - Medium

## Question Details
- **Concept:** `NamedTuple`
- **Supporting Python concepts:** Immutable records, type hints, unpacking
- **Difficulty:** Medium
- **Domain:** Offline GPS readings
- **Learning Objective:** Model a compact immutable GPS record with named fields and validation.

## Scenario
A navigation report consumes fixed prerecorded latitude and longitude readings.

## Function Details
- **Required Python interface:** Define `GPSReading(NamedTuple)` with `latitude: float` and `longitude: float`, plus `make_reading(latitude: float, longitude: float) -> GPSReading`.
- **Behavior:** Validate latitude -90 through 90 and longitude -180 through 180, then return the named tuple rounded to six decimal places.
- **Return shape:** Return an immutable `GPSReading` with named fields.
- **Input rules and constraints:** Coordinates are finite numeric values in their geographic ranges. Additional constraints: Use `typing.NamedTuple`; Do not mutate or add fields after creation; Coordinates are synthetic and offline.

## Tasks to Implement
1. Implement the specified Python interface: Define `GPSReading(NamedTuple)` with `latitude: float` and `longitude: float`, plus `make_reading(latitude: float, longitude: float) -> GPSReading`.
2. Apply the stated input validation and constraints: Coordinates are finite numeric values in their geographic ranges.
3. Implement the required behavior: Validate latitude -90 through 90 and longitude -180 through 180, then return the named tuple rounded to six decimal places.
4. Return the specified result shape without changing the required ordering or formatting: Return an immutable `GPSReading` with named fields.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `reading = make_reading(0, 0); (reading.latitude, reading.longitude)` | `(0, 0)` |
| 2 | `reading = make_reading(90, 180); (reading.latitude, reading.longitude)` | `(90, 180)` |
| 3 | `reading = make_reading(-90, -180); (reading.latitude, reading.longitude)` | `(-90, -180)` |
| 4 | `reading = make_reading(37.7749296, -122.4194154); (reading.latitude, reading.longitude)` | `(37.77493, -122.419415)` |
| 5 | `reading = make_reading(45.1234567, 10.9876543); (reading.latitude, reading.longitude)` | `(45.123457, 10.987654)` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Tuples, type hints, classes, and numeric ranges.

### Rules and Constraints

- Use `typing.NamedTuple`.
- Do not mutate or add fields after creation.
- Coordinates are synthetic and offline.

### Hints

Validate before constructing and use the tuple's named fields in tests.

### Common Mistakes

- Returning a mutable dictionary.
- Allowing out-of-range coordinates.
- Rounding before range validation.

### Extension Challenge

Add an enum for coordinate source quality.
