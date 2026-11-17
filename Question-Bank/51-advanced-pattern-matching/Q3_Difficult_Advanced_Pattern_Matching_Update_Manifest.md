# 51 - Evaluating Nested Update Manifests - Difficult

## Question Details
- **Concept:** Nested mapping patterns with guards
- **Supporting Python concepts:** OR patterns, captures, validation, version checks
- **Difficulty:** Difficult
- **Domain:** Offline software update manifest
- **Learning Objective:** Validate and route nested update manifests with precise structural pattern matching.

## Scenario
A simulator checks a synthetic update manifest before reporting whether it is eligible.

## Function Details
- **Required Python interface:** Implement `evaluate_manifest(manifest: dict[str, object]) -> str`.
- **Behavior:** Match `{"target": {"model": model, "version": version}, "package": package}`. Return `READY:<model>:<version>` when package is `"full"` or `"delta"` and version is a three-integer tuple; a non-empty string package value other than `"full"` or `"delta"` returns `REJECTED_FORMAT`. Non-string or blank package values, and missing or otherwise malformed structure, raise `ValueError`.
- **Return shape:** Return the exact ready or rejected string.
- **Input rules and constraints:** Model and package are non-empty strings; version is `(major, minor, patch)` with non-negative integers. Additional constraints: Use nested mapping patterns and an OR pattern for package values; Do not download, install, or connect to a vehicle; Version tuple length and types must be validated.

## Tasks to Implement
1. Implement the specified Python interface: Implement `evaluate_manifest(manifest: dict[str, object]) -> str`.
2. Apply the stated input validation and constraints: Model and package are non-empty strings; version is `(major, minor, patch)` with non-negative integers.
3. Implement the required behavior: Match `{"target": {"model": model, "version": version}, "package": package}`. Return `READY:<model>:<version>` when package is `"full"` or `"delta"` and version is a three-integer tuple; a non-empty string package value other than `"full"` or `"delta"` returns `REJECTED_FORMAT`. Non-string or blank package values, and missing or otherwise malformed structure, raise `ValueError`.
4. Return the specified result shape without changing the required ordering or formatting: Return the exact ready or rejected string.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `evaluate_manifest({"target": {"model": "EV-A", "version": (1, 2, 3)}, "package": "full"})` | `"READY:EV-A:(1, 2, 3)"` |
| 2 | `evaluate_manifest({"target": {"model": "EV-B", "version": (0, 0, 0)}, "package": "delta"})` | `"READY:EV-B:(0, 0, 0)"` |
| 3 | `evaluate_manifest({"target": {"model": "EV-C", "version": (2, 5, 1)}, "package": "patch"})` | `"REJECTED_FORMAT"` |
| 4 | `evaluate_manifest({"target": {"model": "EV-D", "version": (10, 0, 7)}, "package": "full"})` | `"READY:EV-D:(10, 0, 7)"` |
| 5 | `evaluate_manifest({"target": {"model": "EV-E", "version": (1, 0, 0)}, "package": "delta"})` | `"READY:EV-E:(1, 0, 0)"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Dictionaries, pattern matching, guards, tuples, and validation.

### Rules and Constraints

- Use nested mapping patterns and an OR pattern for package values.
- Do not download, install, or connect to a vehicle.
- Version tuple length and types must be validated.

### Hints

Use a nested mapping case to capture values, then use a guard for package and version rules.

### Common Mistakes

- Accepting a two-part version.
- Treating `patch` as equivalent to `delta`.
- Mutating the manifest during evaluation.

### Extension Challenge

Add a `compatibility` mapping and require its model to match the target model.
