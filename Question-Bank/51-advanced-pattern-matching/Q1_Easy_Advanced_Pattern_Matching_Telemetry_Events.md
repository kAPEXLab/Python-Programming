# 51 - Classifying Telemetry Event Mappings - Easy

## Question Details
- **Concept:** Structural pattern matching
- **Supporting Python concepts:** Mapping patterns, guards, validation
- **Difficulty:** Easy
- **Domain:** Offline telemetry event classification
- **Learning Objective:** Classify event dictionaries with mapping patterns and guarded numeric values.

## Scenario
A replay tool classifies prerecorded speed and battery events.

## Function Details
- **Required Python interface:** Implement `classify_event(event: dict[str, object]) -> str`.
- **Behavior:** Match `{"type":"speed", "value": value}` and return `OVERSPEED` above 120 km/h or `SPEED_OK`; match battery values at least 20 percent as `BATTERY_OK`, otherwise `BATTERY_LOW`.
- **Return shape:** Return the exact classification string.
- **Input rules and constraints:** Event type is `speed` or `battery`; values are numeric and speed is 0 through 300, SOC 0 through 100. Additional constraints: Use mapping patterns and guards; Reject missing or malformed fields with `ValueError`; Events are offline.

## Tasks to Implement
1. Implement the specified Python interface: Implement `classify_event(event: dict[str, object]) -> str`.
2. Apply the stated input validation and constraints: Event type is `speed` or `battery`; values are numeric and speed is 0 through 300, SOC 0 through 100.
3. Implement the required behavior: Match `{"type":"speed", "value": value}` and return `OVERSPEED` above 120 km/h or `SPEED_OK`; match battery values at least 20 percent as `BATTERY_OK`, otherwise `BATTERY_LOW`.
4. Return the specified result shape without changing the required ordering or formatting: Return the exact classification string.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `classify_event({"type": "speed", "value": 120})` | `"SPEED_OK"` |
| 2 | `classify_event({"type": "speed", "value": 120.1})` | `"OVERSPEED"` |
| 3 | `classify_event({"type": "speed", "value": 0})` | `"SPEED_OK"` |
| 4 | `classify_event({"type": "battery", "value": 20})` | `"BATTERY_OK"` |
| 5 | `classify_event({"type": "battery", "value": 19.9})` | `"BATTERY_LOW"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Dictionaries, `match-case`, functions, and validation.

### Rules and Constraints

- Use mapping patterns and guards.
- Reject missing or malformed fields with `ValueError`.
- Events are offline.

### Hints

Validate the mapping shape first through match cases, then apply guards.

### Common Mistakes

- Using chained `if` statements instead of matching.
- Treating missing values as zero.
- Using an exclusive SOC boundary accidentally.

### Extension Challenge

Add a nested `location` mapping and classify events by region.
