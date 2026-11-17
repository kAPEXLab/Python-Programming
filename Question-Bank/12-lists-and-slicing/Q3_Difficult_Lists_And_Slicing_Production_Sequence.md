# 12 - Production Sequence - Difficult

## Question Details
- Concept: Extended list slicing and copy semantics
- Supporting concepts: Validation, transformations, tuples, rounding
- Difficulty: Difficult
- Domain: Offline production station sequence
- Learning Objective: Use extended slices to inspect station batches while producing a validated, non-mutating sequence report.

## Scenario
A factory simulation records station cycle times in seconds. Consecutive records belong to a repeating three-station cycle: weld, paint, and inspection.

## Function Details
- Function signature: `analyze_production_sequence(cycle_times: list[float]) -> dict[str, object]`
- Behavior / return shape: Return the station-specific samples, their rounded averages, and whether the sequence is complete.
- Exact accepted inputs: The list has 0 through 300 finite values from 1.0 through 600.0 seconds. Values are measured to at most two decimals. A complete sequence has a length divisible by three.
- Output and validation / behavior: Use slices `[0::3]`, `[1::3]`, and `[2::3]`. Return `weld_times`, `paint_times`, `inspection_times`, `averages`, and `complete`. `averages` maps each station name to a value rounded to two decimals; an empty station average is `None`.

## Tasks to Implement
1. Implement `analyze_production_sequence` with the exact signature above and validate the inputs against these accepted rules: The list has 0 through 300 finite values from 1.0 through 600.0 seconds. Values are measured to at most two decimals. A complete sequence has a length divisible by three.
2. Return the station-specific samples, their rounded averages, and whether the sequence is complete.
3. Return exactly the specified result: Use slices `[0::3]`, `[1::3]`, and `[2::3]`. Return `weld_times`, `paint_times`, `inspection_times`, `averages`, and `complete`. `averages` maps each station name to a value rounded to two decimals; an empty station average is `None`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | analyze_production_sequence([]) | {"weld_times": [], "paint_times": [], "inspection_times": [], "averages": {"weld": None, "paint": None, "inspection": None}, "complete": True} | Typical valid input. |
| 2 | analyze_production_sequence([1, 2, 3]) | {"weld_times": [1], "paint_times": [2], "inspection_times": [3], "averages": {"weld": 1.0, "paint": 2.0, "inspection": 3.0}, "complete": True} | Valid boundary case. |
| 3 | analyze_production_sequence([1, 2, 3, 4, 5, 6]) | {"weld_times": [1, 4], "paint_times": [2, 5], "inspection_times": [3, 6], "averages": {"weld": 2.5, "paint": 3.5, "inspection": 4.5}, "complete": True} | Checks the threshold rule. |
| 4 | analyze_production_sequence([10, 20]) | {"weld_times": [10], "paint_times": [20], "inspection_times": [], "averages": {"weld": 10.0, "paint": 20.0, "inspection": None}, "complete": False} | Checks an alternate valid shape. |
| 5 | analyze_production_sequence([1.25, 2.5, 3.75, 4.5, 5.5, 6.5, 7.5, 8.5, 9.5]) | {"weld_times": [1.25, 4.5, 7.5], "paint_times": [2.5, 5.5, 8.5], "inspection_times": [3.75, 6.5, 9.5], "averages": {"weld": 4.42, "paint": 5.5, "inspection": 6.58}, "complete": True} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of analyze_production_sequence that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, slicing, dictionaries, tuples, functions, and exceptions.

### Rules and Constraints
- Station names are weld, paint, and inspection.
- complete is true only when the list length is divisible by three.
- Raise ValueError for non-finite or out-of-range values.
- Do not mutate input or use sorting.

### Hints
1. Validate values before slicing.
2. Extended slices select every third item from different offsets.
3. Compute complete from the length, not from the contents.

### Common Mistakes
- Using a step of two.
- Dropping the incomplete tail instead of reporting it.
- Returning averages with inconsistent rounding.

### Extension Challenge
Return the longest station time and its zero-based original index.
