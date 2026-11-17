# 44 - Generating an Import-Safe Fleet Report - Easy

## Question Details
- **Concept:** `if __name__ == "__main__"`
- **Supporting Python concepts:** `pathlib`, `statistics`, import-safe scripts
- **Difficulty:** Easy
- **Domain:** Offline report generation
- **Learning Objective:** Build a script that is reusable when imported and executable when run directly.

## Scenario
A report generator summarizes a fixed set of fleet distances without running work during import.

## Function Details
- **Required Python interface:** Implement `build_report(distances_km: list[float]) -> str` and a guarded `main() -> None`.
- **Behavior:** Return `COUNT=<n>;AVERAGE_KM=<average:.1f>` using `statistics.fmean`. Reject an empty list and negative values.
- **Return shape:** Return one deterministic summary string; `main` prints it only when the file is run as a script.
- **Input rules and constraints:** Distances are finite, non-negative floats in kilometers. Additional constraints: Keep execution behind the main guard; Use the standard library only; No file or vehicle connection is needed.

## Tasks to Implement
1. Implement the specified Python interface: Implement `build_report(distances_km: list[float]) -> str` and a guarded `main() -> None`.
2. Apply the stated input validation and constraints: Distances are finite, non-negative floats in kilometers.
3. Implement the required behavior: Return `COUNT=<n>;AVERAGE_KM=<average:.1f>` using `statistics.fmean`. Reject an empty list and negative values.
4. Return the specified result shape without changing the required ordering or formatting: Return one deterministic summary string; `main` prints it only when the file is run as a script.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `build_report([10.0])` | `"COUNT=1;AVERAGE_KM=10.0"` |
| 2 | `build_report([0.0, 100.0])` | `"COUNT=2;AVERAGE_KM=50.0"` |
| 3 | `build_report([1.25, 2.25, 3.5])` | `"COUNT=3;AVERAGE_KM=2.3"` |
| 4 | `build_report([0.0, 0.0, 0.0])` | `"COUNT=3;AVERAGE_KM=0.0"` |
| 5 | `build_report([10.5, 20.5])` | `"COUNT=2;AVERAGE_KM=15.5"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Functions, imports, lists, `pathlib`, and basic module execution.

### Rules and Constraints

- Keep execution behind the main guard.
- Use the standard library only.
- No file or vehicle connection is needed.

### Hints

Put only the call to `main()` under the guard; imports must remain safe.

### Common Mistakes

- Calling `main()` at import time.
- Using a hand-written average with an empty list.
- Formatting the count as a decimal.

### Extension Challenge

Add a report path using `pathlib.Path` without writing during import.
