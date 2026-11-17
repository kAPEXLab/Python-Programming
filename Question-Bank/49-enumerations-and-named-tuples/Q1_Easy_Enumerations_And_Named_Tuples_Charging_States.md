# 49 - Parsing Charging States into an Enum - Easy

## Question Details
- **Concept:** `Enum`
- **Supporting Python concepts:** Members, comparisons, serialization
- **Difficulty:** Easy
- **Domain:** Offline charging states
- **Learning Objective:** Represent charging modes with a type-safe enumeration.

## Scenario
A prerecorded charging session reports one of a fixed set of states.

## Function Details
- **Required Python interface:** Define `ChargingState(Enum)` with `IDLE`, `PLUGGED`, `CHARGING`, and `COMPLETE`, each using its lowercase name as value, plus `parse_state(text: str) -> ChargingState`.
- **Behavior:** Normalize text and return the matching enum member; raise `ValueError` for unknown text.
- **Return shape:** Return a `ChargingState` member.
- **Input rules and constraints:** Text is a non-empty state name, case-insensitive after stripping. Additional constraints: Compare enum members, not ad hoc strings, after parsing; Keep states finite and deterministic; No charger connection is required.

## Tasks to Implement
1. Implement the specified Python interface: Define `ChargingState(Enum)` with `IDLE`, `PLUGGED`, `CHARGING`, and `COMPLETE`, each using its lowercase name as value, plus `parse_state(text: str) -> ChargingState`.
2. Apply the stated input validation and constraints: Text is a non-empty state name, case-insensitive after stripping.
3. Implement the required behavior: Normalize text and return the matching enum member; raise `ValueError` for unknown text.
4. Return the specified result shape without changing the required ordering or formatting: Return a `ChargingState` member.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `parse_state("idle")` | `ChargingState.IDLE` |
| 2 | `parse_state(" PLUGGED ")` | `ChargingState.PLUGGED` |
| 3 | `parse_state("Charging")` | `ChargingState.CHARGING` |
| 4 | `parse_state("complete")` | `ChargingState.COMPLETE` |
| 5 | `parse_state("IDLE")` | `ChargingState.IDLE` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Classes, strings, functions, and comparisons.

### Rules and Constraints

- Compare enum members, not ad hoc strings, after parsing.
- Keep states finite and deterministic.
- No charger connection is required.

### Hints

Use enum values as the normalized lookup keys.

### Common Mistakes

- Returning the input string.
- Adding a catch-all enum member.
- Forgetting whitespace normalization.

### Extension Challenge

Add a `terminal` property for `IDLE` and `COMPLETE`.
