# 47 - Lazily Filtering Fleet Trips - Difficult

## Question Details
- **Concept:** Generator expressions and composable iterables
- **Supporting Python concepts:** `filter`, `map`, predicates, laziness
- **Difficulty:** Difficult
- **Domain:** Offline fleet filtering
- **Learning Objective:** Compose lazy transformations to select fleet records by battery state and distance.

## Scenario
A fleet analyst wants qualifying prerecorded trips without creating unnecessary intermediate lists.

## Function Details
- **Required Python interface:** Implement `qualifying_trips(records: Iterable[dict[str, object]], minimum_soc: int) -> Iterator[str]`.
- **Behavior:** Yield each `vehicle_id` whose integer `soc` is at least `minimum_soc` and whose `distance_km` exceeds 10.0, in input order.
- **Return shape:** Yield matching vehicle IDs lazily; malformed records raise `ValueError` when reached.
- **Input rules and constraints:** Records contain non-empty string `vehicle_id`, integer `soc` 0 through 100, and non-negative numeric `distance_km`. `minimum_soc` must be an integer from 0 through 100. Additional constraints: Use a generator expression or generator pipeline; Do not sort or materialize the input; All data is offline.

## Tasks to Implement
1. Implement the specified Python interface: Implement `qualifying_trips(records: Iterable[dict[str, object]], minimum_soc: int) -> Iterator[str]`.
2. Apply the stated input validation and constraints: Records contain non-empty string `vehicle_id`, integer `soc` 0 through 100, and non-negative numeric `distance_km`. `minimum_soc` must be an integer from 0 through 100.
3. Implement the required behavior: Yield each `vehicle_id` whose integer `soc` is at least `minimum_soc` and whose `distance_km` exceeds 10.0, in input order.
4. Return the specified result shape without changing the required ordering or formatting: Yield matching vehicle IDs lazily; malformed records raise `ValueError` when reached.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `list(qualifying_trips([{"vehicle_id": "EV-1", "soc": 50, "distance_km": 10.01}], 50))` | `["EV-1"]` |
| 2 | `list(qualifying_trips([{"vehicle_id": "EV-2", "soc": 100, "distance_km": 10.0}], 0))` | `[]` |
| 3 | `list(qualifying_trips([{"vehicle_id": "EV-3", "soc": 49, "distance_km": 100}], 50))` | `[]` |
| 4 | `list(qualifying_trips([{"vehicle_id": "EV-4", "soc": 0, "distance_km": 11}], 0))` | `["EV-4"]` |
| 5 | `list(qualifying_trips([{"vehicle_id": "EV-5", "soc": 80, "distance_km": 12}, {"vehicle_id": "EV-6", "soc": 80, "distance_km": 20}], 80))` | `["EV-5", "EV-6"]` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Generator expressions, dictionaries, iterables, predicates, and numeric validation.

### Rules and Constraints

- Use a generator expression or generator pipeline.
- Do not sort or materialize the input.
- All data is offline.

### Hints

Validate each record inside the generator so evaluation remains lazy.

### Common Mistakes

- Building a list before returning.
- Using `>=` for the distance condition.
- Validating records that the consumer never reaches.

### Extension Challenge

Accept a predicate callback for custom fleet policies.
