# 27 - Sorting Searching Aggregation Filtering Mapping Reduction Sensor Statistics - Medium

## Question Details
- **Concept:** Sorting, searching, aggregation, filtering, mapping, and reduction
- **Supporting Python concepts:** Statistics, predicates, stable output
- **Difficulty:** Medium
- **Domain:** Offline sensor statistics
- **Learning Objective:** Filter valid readings and reduce them into deterministic minimum, maximum, and average statistics.
- **Estimated completion time:** 55 minutes

## Scenario
A simulated pressure sensor reports readings, including a sentinel for missing samples.

## Function Details
Implement `sensor_statistics(readings: list[float]) -> dict[str, float]`.

**Required API / operation:** Summarize all valid tire-pressure readings within the permitted range.

**Input rules and constraints:** Valid readings are 0.0 through 100.0 kPa. The sentinel `-1.0` means missing. All other out-of-range values are invalid and should raise `ValueError`.

**Behavior and return shape:** Return `{"min": value, "max": value, "average": value}` with values rounded to one decimal place. Raise `ValueError` when no valid reading remains.

**Implementation rules:** Filter only the documented sentinel. Do not sort or mutate the original list. Use all valid readings for the average.

## Tasks to Implement
1. Filter valid readings and reduce them into deterministic minimum, maximum, and average statistics.
2. Summarize all valid tire-pressure readings within the permitted range.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `readings=[-1.0, 50.0]` | `{'min': 50.0, 'max': 50.0, 'average': 50.0}` |
| 2 | `readings=[0.0, 100.0]` | `{'min': 0.0, 'max': 100.0, 'average': 50.0}` |
| 3 | `readings=[10.04, 10.05, 10.07]` | `{'min': 10.0, 'max': 10.1, 'average': 10.1}` |
| 4 | `readings=[20.0, -1.0, 40.0]` | `{'min': 20.0, 'max': 40.0, 'average': 30.0}` |
| 5 | `readings=[1.1, 2.2, 3.3, 4.4]` | `{'min': 1.1, 'max': 4.4, 'average': 2.8}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, lists, filtering, sorting, and arithmetic.

### Rules and Constraints
- Filter only the documented sentinel.
- Do not sort or mutate the original list.
- Use all valid readings for the average.

### Hints
1. Validate non-sentinel values while filtering.
2. Use `min`, `max`, and `sum`.
3. Round only the result dictionary values.

### Common Mistakes
- Silently dropping all out-of-range values.
- Including the sentinel in the average.
- Returning integer-looking values inconsistently.

### Extension Challenge
Add median and sample count without changing the original keys.
