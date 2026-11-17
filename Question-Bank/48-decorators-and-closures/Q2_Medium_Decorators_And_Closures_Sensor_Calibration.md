# 48 - Applying a Sensor Calibration Decorator - Medium

## Question Details
- **Concept:** Parameterized decorators and closures
- **Supporting Python concepts:** Factory functions, numeric transformation, metadata
- **Difficulty:** Medium
- **Domain:** Offline sensor calibration
- **Learning Objective:** Create a configurable decorator that applies a fixed calibration offset.

## Scenario
A test harness calibrates prerecorded sensor readings before a check consumes them.

## Function Details
- **Required Python interface:** Implement `calibrated(offset: float) -> Callable` for functions accepting one numeric reading.
- **Behavior:** The decorated function must receive `reading + offset`, return its result, reject a non-finite offset at decoration time, and reject non-finite readings when the wrapper is called.
- **Return shape:** Return exactly the wrapped function's result after calibration.
- **Input rules and constraints:** Offset and readings are finite numbers; booleans are not valid numeric readings or offsets. Additional constraints: Store offset in a closure; Preserve wrapped metadata; Never mutate caller-owned collections.

## Tasks to Implement
1. Implement the specified Python interface: Implement `calibrated(offset: float) -> Callable` for functions accepting one numeric reading.
2. Apply the stated input validation and constraints: Offset and readings are finite numbers; booleans are not valid numeric readings or offsets.
3. Implement the required behavior: The decorated function must receive `reading + offset`, return its result, reject a non-finite offset at decoration time, and reject non-finite readings when the wrapper is called.
4. Return the specified result shape without changing the required ordering or formatting: Return exactly the wrapped function's result after calibration.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `@calibrated(1.5) around lambda x: x; call with 2.0` | `3.5` |
| 2 | `@calibrated(-2.0) around lambda x: x * 2; call with 5.0` | `6.0` |
| 3 | `@calibrated(0.0) around lambda x: round(x, 1); call with 1.25` | `1.2` |
| 4 | `@calibrated(0.25) around lambda x: x >= 10; call with 9.75` | `True` |
| 5 | `@calibrated(10.0) around lambda x: f"{x:.1f}"; call with 0.5` | `"10.5"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Decorators, closures, functions, numeric types, and validation.

### Rules and Constraints

- Store offset in a closure.
- Preserve wrapped metadata.
- Never mutate caller-owned collections.

### Hints

The outer function validates and captures offset; the inner wrapper adjusts the argument.

### Common Mistakes

- Applying the offset after the wrapped function runs.
- Reusing one mutable offset across decorators.
- Accepting `nan`.

### Extension Challenge

Support separate scale and offset parameters.
