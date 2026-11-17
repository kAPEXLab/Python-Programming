# 36 - Immutable Telemetry Windows - Difficult

## Question Details
- **Concept:** Operator overloading
- **Supporting Python concepts:** Sequence protocol, slicing, iteration, immutability, type hints
- **Difficulty:** Difficult
- **Domain:** Offline telemetry window analysis
- **Learning Objective:** Implement a small sequence-like object with predictable indexing and concatenation.

## Scenario
A diagnostic tool groups a fixed window of sensor samples for repeatable offline analysis.

## Function Details
- **Required Python interface:** Implement `TelemetryWindow(values: tuple[float, ...])` with `__len__`, `__getitem__`, `__iter__`, `__add__`, and `average()`.
- **Behavior:** Indexing returns a float; slicing returns a new window; adding another window concatenates values. Average an empty window is invalid. Round average to two decimals.
- **Return shape:** Support integer indices, slices, iteration, concatenation, and numeric average.
- **Input rules and constraints:** Values must be finite numbers. The constructor accepts a tuple and stores immutable data. Additional constraints: Do not expose a mutable internal list; Unrelated addition operands should return `NotImplemented`; Raise `ValueError` for empty averages or invalid values.

## Tasks to Implement
1. Implement the specified Python interface: Implement `TelemetryWindow(values: tuple[float, ...])` with `__len__`, `__getitem__`, `__iter__`, `__add__`, and `average()`.
2. Apply the stated input validation and constraints: Values must be finite numbers. The constructor accepts a tuple and stores immutable data.
3. Implement the required behavior: Indexing returns a float; slicing returns a new window; adding another window concatenates values. Average an empty window is invalid. Round average to two decimals.
4. Return the specified result shape without changing the required ordering or formatting: Support integer indices, slices, iteration, concatenation, and numeric average.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `TelemetryWindow((1.0, 2.0, 3.0))[0]` | `1.0` |
| 2 | `tuple(TelemetryWindow((1.0, 2.0, 3.0))[1:])` | `(2.0, 3.0)` |
| 3 | `tuple(TelemetryWindow((1.0, 2.0)) + TelemetryWindow((3.0,)))` | `(1.0, 2.0, 3.0)` |
| 4 | `TelemetryWindow((2.0, 4.0, 6.0)).average()` | `4.0` |
| 5 | `tuple(TelemetryWindow(()))` | `()` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Classes, special methods, lists, slicing, and exceptions.

### Rules and Constraints

- Do not expose a mutable internal list.
- Unrelated addition operands should return `NotImplemented`.
- Raise `ValueError` for empty averages or invalid values.

### Hints

Delegate indexing and slicing to the tuple, wrapping slices in a new object.

### Common Mistakes

- Returning a list for slices.
- Allowing mutable state changes.
- Dividing by zero for an empty window.

### Extension Challenge

Add a `delta()` method that returns adjacent differences.
