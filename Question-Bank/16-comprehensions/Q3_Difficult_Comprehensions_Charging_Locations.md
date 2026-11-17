# 16 - Charging Locations - Difficult

## Question Details
- Concept: Nested comprehensions
- Supporting concepts: Nested dictionaries, filtering, sorting, validation
- Difficulty: Difficult
- Domain: Simulated charging location catalog
- Learning Objective: Use nested comprehensions to flatten and filter charging connector data.

## Scenario
An offline catalog groups charging connectors by location and connector type.

## Function Details
- Function signature: `available_charging_locations(locations: dict[str, list[dict[str, object]]], connector: str) -> list[str]`
- Behavior / return shape: Return sorted locations that offer a requested connector with at least one operational port.
- Exact accepted inputs: Location names are non-empty strings. Each connector record has `type` (`AC` or `DC`), `ports` (integer 0 through 20), and `operational` (boolean). The requested connector is `AC` or `DC`, case-insensitive.
- Output and validation / behavior: Return location names sorted alphabetically where at least one matching connector has `ports > 0` and `operational is True`.

## Tasks to Implement
1. Implement `available_charging_locations` with the exact signature above and validate the inputs against these accepted rules: Location names are non-empty strings. Each connector record has `type` (`AC` or `DC`), `ports` (integer 0 through 20), and `operational` (boolean). The requested connector is `AC` or `DC`, case-insensitive.
2. Return sorted locations that offer a requested connector with at least one operational port.
3. Implement this output contract exactly: Return location names sorted alphabetically where at least one matching connector has `ports > 0` and `operational is True`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | available_charging_locations({"Depot": [{"type": "AC", "ports": 2, "operational": True}]}, "AC") | ["Depot"] | Typical valid input. |
| 2 | available_charging_locations({"A": [{"type": "DC", "ports": 0, "operational": True}], "B": [{"type": "DC", "ports": 1, "operational": True}]}, "dc") | ["B"] | Valid boundary case. |
| 3 | available_charging_locations({"Z": [{"type": "AC", "ports": 1, "operational": False}], "A": [{"type": "AC", "ports": 2, "operational": True}]}, "AC") | ["A"] | Checks the threshold rule. |
| 4 | available_charging_locations({}, "DC") | [] | Checks an alternate valid shape. |
| 5 | available_charging_locations({"Shop": [{"type": "AC", "ports": 1, "operational": True}, {"type": "DC", "ports": 3, "operational": True}]}, "DC") | ["Shop"] | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of available_charging_locations that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Comprehensions, nested collections, dictionaries, strings, sorting, and validation.

### Rules and Constraints
- Use a comprehension to inspect nested connector records.
- Use a separate filtering step or comprehension for the final list.
- Raise ValueError for malformed data; do not mutate input.

### Hints
1. Normalize the requested connector once.
2. Validate every nested record before filtering.
3. Require all three availability conditions in the predicate.

### Common Mistakes
- Treating non-operational ports as usable.
- Returning locations in dictionary insertion order.
- Matching AC against every connector type.

### Extension Challenge
Return (location, connector_type, ports) tuples for each matching connector.
