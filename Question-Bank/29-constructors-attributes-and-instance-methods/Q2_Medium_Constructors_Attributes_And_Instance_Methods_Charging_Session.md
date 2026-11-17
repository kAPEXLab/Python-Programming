# 29 - Constructors Attributes and Instance Methods Charging Session - Medium

## Question Details
- **Concept:** Constructors, attributes, and instance methods
- **Supporting Python concepts:** State changes, percentages, guards
- **Difficulty:** Medium
- **Domain:** Offline charging-session state
- **Learning Objective:** Use instance methods to update a validated charging-session object safely.
- **Estimated completion time:** 50 minutes

## Scenario
A simulator tracks a session's initial SOC and current SOC as charging energy is applied.

## Function Details
Implement class `ChargingSession` with `__init__(self, initial_soc: float)` and `add_soc(self, increase: float) -> float`.

**Required API / operation:** Create a session and increase its SOC without exceeding 100%.

**Input rules and constraints:** Initial SOC is 0 through 100. Each increase is positive and at most 100 percentage points.

**Behavior and return shape:** `add_soc` updates the instance and returns the new SOC rounded to one decimal. Reject an increase that would exceed 100.

**Implementation rules:** Store current SOC as an instance attribute. Raise `ValueError` for invalid construction or updates. This object simulates state only.

## Tasks to Implement
1. Use instance methods to update a validated charging-session object safely.
2. Create a session and increase its SOC without exceeding 100%.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `session=ChargingSession(0); session.add_soc(1)` | `1.0` |
| 2 | `session=ChargingSession(50); session.add_soc(25)` | `75.0` |
| 3 | `session=ChargingSession(99); session.add_soc(1)` | `100.0` |
| 4 | `session=ChargingSession(20); session.add_soc(0.26)` | `20.3` |
| 5 | `session=ChargingSession(0); session.add_soc(100)` | `100.0` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, attributes, methods, conditionals, and exceptions.

### Rules and Constraints
- Store current SOC as an instance attribute.
- Raise `ValueError` for invalid construction or updates.
- This object simulates state only.

### Hints
1. Validate the proposed new value before assignment.
2. Keep current SOC separate from the initial value.
3. Return the updated attribute.

### Common Mistakes
- Silently clamping overcharge to 100.
- Updating before validating.
- Using a class-level SOC.

### Extension Challenge
Add a `finish()` method that rejects sessions below a minimum target SOC.
