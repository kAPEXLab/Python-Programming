# 43 - Dispatching to Telemetry Reader Modules - Difficult

## Question Details
- **Concept:** Package-relative imports
- **Supporting Python concepts:** Reader protocols, parsing, package API boundaries
- **Difficulty:** Difficult
- **Domain:** Offline telemetry readers
- **Learning Objective:** Combine specialized readers through package-relative imports while preserving a stable public API.

## Scenario
An offline telemetry package reads text samples from battery and tire-pressure sources.

## Function Details
- **Required Python interface:** Implement `read_sample(source: str, payload: str) -> tuple[str, float]` in a package that delegates to source-specific reader modules.
- **Behavior:** For `battery`, parse a voltage such as `"12.60V"`; for `tire`, parse pressure such as `"2.40bar"`. Return `(source, value)` rounded to two places.
- **Return shape:** Return a tuple like `("battery", 12.6)` or `("tire", 2.4)`.
- **Input rules and constraints:** Source is `battery` or `tire`; payload contains the exact unit suffix and a finite non-negative number. Additional constraints: Use relative imports between package modules; Reject unknown sources and malformed units with `ValueError`; Samples are prerecorded and offline.

## Tasks to Implement
1. Implement the specified Python interface: Implement `read_sample(source: str, payload: str) -> tuple[str, float]` in a package that delegates to source-specific reader modules.
2. Apply the stated input validation and constraints: Source is `battery` or `tire`; payload contains the exact unit suffix and a finite non-negative number.
3. Implement the required behavior: For `battery`, parse a voltage such as `"12.60V"`; for `tire`, parse pressure such as `"2.40bar"`. Return `(source, value)` rounded to two places.
4. Return the specified result shape without changing the required ordering or formatting: Return a tuple like `("battery", 12.6)` or `("tire", 2.4)`.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `read_sample("battery", "12.60V")` | `("battery", 12.6)` |
| 2 | `read_sample("tire", "2.40bar")` | `("tire", 2.4)` |
| 3 | `read_sample("battery", "0V")` | `("battery", 0.0)` |
| 4 | `read_sample("tire", "35bar")` | `("tire", 35.0)` |
| 5 | `read_sample("battery", "14.256V")` | `("battery", 14.26)` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Packages, relative imports, functions, protocols, and validation.

### Rules and Constraints

- Use relative imports between package modules.
- Reject unknown sources and malformed units with `ValueError`.
- Samples are prerecorded and offline.

### Hints

Keep unit parsing inside each reader and dispatch from one package-level function.

### Common Mistakes

- Accepting a battery payload for the tire reader.
- Using absolute imports that only work from one directory.
- Returning the raw payload.

### Extension Challenge

Add a `temperature` reader for payloads ending in `C`.
