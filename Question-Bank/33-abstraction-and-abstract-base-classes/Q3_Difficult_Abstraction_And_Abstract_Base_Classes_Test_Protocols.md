# 33 - Abstraction and Abstract Base Classes Test Protocols - Difficult

## Question Details
- **Concept:** Abstract base classes
- **Supporting Python concepts:** Protocol design, result objects, validation, sequencing
- **Difficulty:** Difficult
- **Domain:** Offline vehicle test protocols
- **Learning Objective:** Design abstract test protocols that share execution orchestration while specializing their checks.
- **Estimated completion time:** 65 minutes

## Scenario
A simulated quality harness runs braking and charging checks against a fixed observation record.

## Function Details
Implement `run_protocols(protocols: list[TestProtocol], observation: dict[str, float]) -> list[tuple[str, bool]]`, preserving protocol order. Missing required fields must raise `KeyError`.

**Required API / operation:** Define abstract `TestProtocol` with `name` and `evaluate(observation: dict[str, float]) -> bool`. Implement `BrakeProtocol` requiring `brake_pressure_bar >= 30`, and `ChargeProtocol` requiring `charge_current_a <= 32`.

**Input rules and constraints:** Protocols must be non-empty. Brake pressure and charge current are finite numbers when present.

**Behavior and return shape:** Return `(protocol.name, passed)` pairs. A failed condition returns `False`, not an exception. Set `BrakeProtocol.name` to `"BrakeProtocol"` and `ChargeProtocol.name` to `"ChargeProtocol"`.

**Implementation rules:** `evaluate` must be abstract. Validate numeric observations before evaluation. Use Python 3.12+ and no real test equipment.

## Tasks to Implement
1. Design abstract test protocols that share execution orchestration while specializing their checks.
2. Define abstract `TestProtocol` with `name` and `evaluate(observation: dict[str, float]) -> bool`. Implement `BrakeProtocol` requiring `brake_pressure_bar >= 30`, and `ChargeProtocol` requiring `charge_current_a <= 32`.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `run_protocols([BrakeProtocol()], {'brake_pressure_bar': 30})` | `[('BrakeProtocol', True)]` |
| 2 | `run_protocols([BrakeProtocol()], {'brake_pressure_bar': 29.9})` | `[('BrakeProtocol', False)]` |
| 3 | `run_protocols([ChargeProtocol()], {'charge_current_a': 32})` | `[('ChargeProtocol', True)]` |
| 4 | `run_protocols([ChargeProtocol()], {'charge_current_a': 32.1})` | `[('ChargeProtocol', False)]` |
| 5 | `run_protocols([ChargeProtocol(), BrakeProtocol()], {'charge_current_a': 20, 'brake_pressure_bar': 40})` | `[('ChargeProtocol', True), ('BrakeProtocol', True)]` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
ABC syntax, inheritance, dictionaries, loops, and boolean logic.

### Rules and Constraints
- `evaluate` must be abstract.
- Validate numeric observations before evaluation.
- Use Python 3.12+ and no real test equipment.

### Hints
Keep orchestration generic and let each protocol own its required field.

### Common Mistakes
- Returning only booleans and losing protocol names.
- Treating failed checks as errors.
- Hiding missing fields with defaults.

### Extension Challenge
Add a tire-pressure protocol with four required wheel fields.
