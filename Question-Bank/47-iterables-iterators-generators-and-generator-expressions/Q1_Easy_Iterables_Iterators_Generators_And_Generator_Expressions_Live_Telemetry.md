# 47 - Selecting the First Valid Speed - Easy

## Question Details
- **Concept:** Iterables and iterators
- **Supporting Python concepts:** `iter`, `next`, protocols, sentinels
- **Difficulty:** Easy
- **Domain:** Offline live-telemetry replay
- **Learning Objective:** Consume a finite telemetry iterable one sample at a time without indexing assumptions.

## Scenario
A replay tool presents prerecorded speed samples through the iterator protocol.

## Function Details
- **Required Python interface:** Implement `first_valid_speed(samples: Iterable[float]) -> float`.
- **Behavior:** Return the first finite speed from 0 through 300 km/h, consuming samples in order. Raise `ValueError` if none qualifies.
- **Return shape:** Return the first valid speed unchanged.
- **Input rules and constraints:** Any iterable of numeric values; invalid values are skipped. Additional constraints: Do not require a list or use indexing; Consume lazily until a result is found; Replay data is offline.

## Tasks to Implement
1. Implement the specified Python interface: Implement `first_valid_speed(samples: Iterable[float]) -> float`.
2. Apply the stated input validation and constraints: Any iterable of numeric values; invalid values are skipped.
3. Implement the required behavior: Return the first finite speed from 0 through 300 km/h, consuming samples in order. Raise `ValueError` if none qualifies.
4. Return the specified result shape without changing the required ordering or formatting: Return the first valid speed unchanged.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `first_valid_speed([0.0])` | `0.0` |
| 2 | `first_valid_speed([301.0, 120.5])` | `120.5` |
| 3 | `first_valid_speed(iter([float("nan"), 300.0]))` | `300.0` |
| 4 | `first_valid_speed((80.0, 90.0, 100.0))` | `80.0` |
| 5 | `first_valid_speed(iter([float("inf"), -1, 42.25]))` | `42.25` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Lists, tuples, loops, functions, and exceptions.

### Rules and Constraints

- Do not require a list or use indexing.
- Consume lazily until a result is found.
- Replay data is offline.

### Hints

Use a `for` loop over the iterable and validate each value before returning.

### Common Mistakes

- Calling `len` on every iterable.
- Materializing an infinite source.
- Treating `None` as zero.

### Extension Challenge

Return the sample index alongside the speed without indexing the source.
