# 43 - Building a Diagnostic Toolkit Package - Medium

## Question Details
- **Concept:** Package structure and re-exports
- **Supporting Python concepts:** `__init__.py`, submodules, public API design
- **Difficulty:** Medium
- **Domain:** Offline diagnostic toolkit
- **Learning Objective:** Design a small package that exposes a clean diagnostic API over specialized submodules.

## Scenario
A diagnostic toolkit package separates code lookup from severity classification.

## Function Details
- **Required Python interface:** Create package modules `codes.py` and `severity.py`, then expose `describe_code(code: str) -> str` from the package.
- **Behavior:** Map `P0420` to `CATALYST_EFFICIENCY`, `P0301` to `CYLINDER_1_MISFIRE`, and unknown codes to `UNKNOWN_CODE`. Normalize case and whitespace.
- **Return shape:** Return the exact symbolic description as a string.
- **Input rules and constraints:** `code` must be a non-empty string containing a diagnostic code. Additional constraints: The package root must re-export the public function; Keep code data in its own submodule; No live diagnostic interface is permitted.

## Tasks to Implement
1. Implement the specified Python interface: Create package modules `codes.py` and `severity.py`, then expose `describe_code(code: str) -> str` from the package.
2. Apply the stated input validation and constraints: `code` must be a non-empty string containing a diagnostic code.
3. Implement the required behavior: Map `P0420` to `CATALYST_EFFICIENCY`, `P0301` to `CYLINDER_1_MISFIRE`, and unknown codes to `UNKNOWN_CODE`. Normalize case and whitespace.
4. Return the specified result shape without changing the required ordering or formatting: Return the exact symbolic description as a string.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `describe_code("P0420")` | `"CATALYST_EFFICIENCY"` |
| 2 | `describe_code(" p0301 ")` | `"CYLINDER_1_MISFIRE"` |
| 3 | `describe_code("p9999")` | `"UNKNOWN_CODE"` |
| 4 | `describe_code("P0420 ")` | `"CATALYST_EFFICIENCY"` |
| 5 | `describe_code("B0001")` | `"UNKNOWN_CODE"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Modules, imports, dictionaries, functions, and exceptions.

### Rules and Constraints

- The package root must re-export the public function.
- Keep code data in its own submodule.
- No live diagnostic interface is permitted.

### Hints

Normalize once at the package boundary and use a dictionary lookup.

### Common Mistakes

- Importing from a file path instead of the package API.
- Mutating the code catalog during lookup.
- Raising for every unknown code.

### Extension Challenge

Expose `severity_for(code: str) -> str` from a second package submodule.
