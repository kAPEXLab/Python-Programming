# 14 - Common Vehicle Features - Difficult

## Question Details
- Concept: Set intersection across collections
- Supporting concepts: Nested lists, normalization, validation, functions
- Difficulty: Difficult
- Domain: Simulated fleet feature analysis
- Learning Objective: Find features common to every vehicle and features appearing in at least two vehicles.

## Scenario
An offline fleet catalog stores feature labels for each vehicle model.

## Function Details
- Function signature: `analyze_common_features(vehicle_features: list[list[str]]) -> dict[str, object]`
- Behavior / return shape: Analyze shared and repeated features without allowing capitalization or whitespace to change identity.
- Exact accepted inputs: There are 0 through 1,000 vehicles, each with 0 through 200 feature names. Names are non-empty strings of letters, digits, spaces, and hyphens.
- Output and validation / behavior: Return `common_to_all` as the intersection of all vehicle sets, `in_at_least_two` as the union of features whose vehicle count is at least two, and `vehicle_count`. Normalize feature names to title case after trimming repeated internal spaces.

## Tasks to Implement
1. Implement `analyze_common_features` with the exact signature above and validate the inputs against these accepted rules: There are 0 through 1,000 vehicles, each with 0 through 200 feature names. Names are non-empty strings of letters, digits, spaces, and hyphens.
2. Analyze shared and repeated features without allowing capitalization or whitespace to change identity.
3. Implement this output contract exactly: Return `common_to_all` as the intersection of all vehicle sets, `in_at_least_two` as the union of features whose vehicle count is at least two, and `vehicle_count`. Normalize feature names to title case after trimming repeated internal spaces.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | analyze_common_features([["ABS", "Air Bag"], ["ABS", "air bag"]]) | {"common_to_all": {"Abs", "Air Bag"}, "in_at_least_two": {"Abs", "Air Bag"}, "vehicle_count": 2} | Typical valid input. |
| 2 | analyze_common_features([]) | {"common_to_all": set(), "in_at_least_two": set(), "vehicle_count": 0} | Valid boundary case. |
| 3 | analyze_common_features([["ABS", "AC"], ["AC", "TPMS"], ["AC"]]) | {"common_to_all": {"Ac"}, "in_at_least_two": {"Ac"}, "vehicle_count": 3} | Checks the threshold rule. |
| 4 | analyze_common_features([["A", "B"], ["B", "C"]]) | {"common_to_all": {"B"}, "in_at_least_two": {"B"}, "vehicle_count": 2} | Checks an alternate valid shape. |
| 5 | analyze_common_features([["Heated  Seat", "ABS"], ["heated seat", "abs"]]) | {"common_to_all": {"Heated Seat", "Abs"}, "in_at_least_two": {"Heated Seat", "Abs"}, "vehicle_count": 2} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of analyze_common_features that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Sets, nested collections, strings, loops, and validation.

### Rules and Constraints
- An empty fleet returns empty sets.
- A one-vehicle fleet has every feature in both result sets.
- Use sets for per-vehicle identity and counting.
- Reject malformed values with ValueError; do not mutate input.

### Hints
1. Normalize each vehicle into a set before analysis.
2. Start the all-vehicle intersection from the first set.
3. Count each feature at most once per vehicle.

### Common Mistakes
- Counting duplicate labels twice for one vehicle.
- Treating empty fleet intersection as a universal set.
- Using case-sensitive feature matching.

### Extension Challenge
Return the features present in exactly one vehicle as a third set.
