# 22 - Type Hints Docstrings and Pure Functions Diagnostic Library - Difficult

## Question Details
- **Concept:** Type hints, docstrings, and pure functions
- **Supporting Python concepts:** Dictionaries, optional values, lookup rules
- **Difficulty:** Difficult
- **Domain:** Offline diagnostic-code descriptions
- **Learning Objective:** Use typed inputs and outputs to create a predictable diagnostic lookup function.
- **Estimated completion time:** 40 minutes

## Scenario
A workshop simulator stores a small library of fault codes and descriptions. A lookup must not access a real diagnostic network.

## Function Details
Implement `describe_code(code: str, library: dict[str, str]) -> str` with a docstring.

**Required API / operation:** Look up a normalized code and produce a fallback message for an unknown but well-formed code.

**Input rules and constraints:** Code must be a non-empty string of 2 to 8 letters, digits, or hyphens. Normalize it by trimming and uppercasing. Library keys are expected to be uppercase.

**Behavior and return shape:** Return the matching description, or `Unknown diagnostic code: CODE` when the code is absent.

**Implementation rules:** Do not mutate the library. Reject non-string codes, malformed codes, or non-string library keys and values with `ValueError`. The function must be deterministic and side-effect free.

## Tasks to Implement
1. Use typed inputs and outputs to create a predictable diagnostic lookup function.
2. Look up a normalized code and produce a fallback message for an unknown but well-formed code.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `code='p0420', library={'P0420': 'Catalyst efficiency low'}` | `'Catalyst efficiency low'` |
| 2 | `code='  bms-01 ', library={'BMS-01': 'Cell imbalance'}` | `'Cell imbalance'` |
| 3 | `code='P0001', library={}` | `'Unknown diagnostic code: P0001'` |
| 4 | `code='AB', library={'AB': 'Known', 'XY': 'Other'}` | `'Known'` |
| 5 | `code='a-9', library={'A-9': 'Nine'}` | `'Nine'` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, dictionaries, strings, `None`, and validation.

### Rules and Constraints
- Do not mutate the library.
- Reject non-string codes, malformed codes, or non-string library keys and values with `ValueError`.
- The function must be deterministic and side-effect free.

### Hints
1. Validate the code before normalizing it.
2. Use `dict.get` or membership testing for the fallback.
3. Preserve the caller's dictionary.

### Common Mistakes
- Looking up the unnormalized code.
- Returning `None` for an unknown code.
- Silently accepting invalid library entries.

### Extension Challenge
Add a pure function that returns all library codes sorted alphabetically.
