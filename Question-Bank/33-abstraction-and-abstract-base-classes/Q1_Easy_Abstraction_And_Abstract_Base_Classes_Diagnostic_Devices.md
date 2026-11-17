# 33 - Abstraction and Abstract Base Classes Diagnostic Devices - Easy

## Question Details
- **Concept:** Abstract base classes
- **Supporting Python concepts:** Inheritance, abstract methods, type hints, validation
- **Difficulty:** Easy
- **Domain:** Offline diagnostic device adapters
- **Learning Objective:** Define an abstract diagnostic contract and implement multiple concrete devices.
- **Estimated completion time:** 55 minutes

## Scenario
A workshop simulator accepts diagnostic devices that expose a common scan operation.

## Function Details
Implement `run_scan(device: DiagnosticDevice, code: str) -> str`, validating that the code is a non-empty uppercase alphanumeric string.

**Required API / operation:** Define abstract `DiagnosticDevice` with `scan(code: str) -> str`. Implement `OBDReader` and `CANReader`; OBD returns `OBD:<code>` and CAN returns `CAN:<code>`.

**Input rules and constraints:** Codes have 2 to 8 characters. Whitespace-only, lowercase, or non-string codes are invalid.

**Behavior and return shape:** Return the concrete device prefix followed by the code.

**Implementation rules:** Mark `scan` abstract and prevent direct construction of the abstract class. Raise `ValueError` for invalid codes. Simulation only; do not open a vehicle connection.

## Tasks to Implement
1. Define an abstract diagnostic contract and implement multiple concrete devices.
2. Define abstract `DiagnosticDevice` with `scan(code: str) -> str`. Implement `OBDReader` and `CANReader`; OBD returns `OBD:<code>` and CAN returns `CAN:<code>`.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `run_scan(OBDReader(), 'P0420')` | `'OBD:P0420'` |
| 2 | `run_scan(CANReader(), 'BMS01')` | `'CAN:BMS01'` |
| 3 | `run_scan(OBDReader(), 'AB')` | `'OBD:AB'` |
| 4 | `run_scan(CANReader(), '12345678')` | `'CAN:12345678'` |
| 5 | `run_scan(OBDReader(), 'A1B2')` | `'OBD:A1B2'` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Classes, inheritance, exceptions, and basic type annotations.

### Rules and Constraints
- Mark `scan` abstract and prevent direct construction of the abstract class.
- Raise `ValueError` for invalid codes.
- Simulation only; do not open a vehicle connection.

### Hints
Use `abc.ABC` and `abc.abstractmethod`.

### Common Mistakes
- Leaving the abstract method concrete.
- Accepting lowercase codes silently.
- Mixing validation with device-specific formatting.

### Extension Challenge
Add a `UDSReader` with a `UDS:` prefix.
