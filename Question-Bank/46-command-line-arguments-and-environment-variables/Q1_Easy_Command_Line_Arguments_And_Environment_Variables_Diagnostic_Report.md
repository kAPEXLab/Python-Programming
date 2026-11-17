# 46 - Parsing Diagnostic Report Arguments - Easy

## Question Details
- **Concept:** `argparse` and environment variables
- **Supporting Python concepts:** Defaults, parsing, required values
- **Difficulty:** Easy
- **Domain:** Offline diagnostic report
- **Learning Objective:** Parse a report vehicle ID from command-line arguments with an environment fallback.

## Scenario
A local diagnostic script needs a vehicle identifier without contacting a vehicle.

## Function Details
- **Required Python interface:** Implement `parse_report_args(argv: list[str], environ: Mapping[str, str]) -> str`.
- **Behavior:** Accept optional `--vehicle-id`; if absent use `DIAGNOSTIC_VEHICLE_ID`. Return the identifier or raise `ValueError` when missing or blank.
- **Return shape:** Return the stripped vehicle identifier.
- **Input rules and constraints:** Arguments are shell-like strings; the environment mapping contains optional text values. Additional constraints: Use `argparse`; do not manually index `argv`; Translate `argparse` parse errors, including unknown or malformed arguments, into `ValueError`; Explicit command-line input wins over the environment; No live diagnostic access is needed.

## Tasks to Implement
1. Implement the specified Python interface: Implement `parse_report_args(argv: list[str], environ: Mapping[str, str]) -> str`.
2. Apply the stated input validation and constraints: Arguments are shell-like strings; the environment mapping contains optional text values.
3. Implement the required behavior: Accept optional `--vehicle-id`; if absent use `DIAGNOSTIC_VEHICLE_ID`. Return the identifier or raise `ValueError` when missing or blank.
4. Return the specified result shape without changing the required ordering or formatting: Return the stripped vehicle identifier.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `parse_report_args(["--vehicle-id", "EV-1"], {})` | `"EV-1"` |
| 2 | `parse_report_args([], {"DIAGNOSTIC_VEHICLE_ID": "EV-2"})` | `"EV-2"` |
| 3 | `parse_report_args(["--vehicle-id", "  EV-3  "], {"DIAGNOSTIC_VEHICLE_ID": "EV-X"})` | `"EV-3"` |
| 4 | `parse_report_args(["--vehicle-id", "FLEET-10"], {})` | `"FLEET-10"` |
| 5 | `parse_report_args([], {"DIAGNOSTIC_VEHICLE_ID": "  UNIT-5 "})` | `"UNIT-5"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Functions, lists, `argparse`, and mappings.

### Rules and Constraints

- Use `argparse`; do not manually index `argv`.
- Translate `argparse` parse errors, including unknown or malformed arguments, into `ValueError`.
- Explicit command-line input wins over the environment.
- No live diagnostic access is needed.

### Hints

Use `parser.parse_args(argv)` and inspect the parsed namespace.

### Common Mistakes

- Reading `sys.argv` inside the function.
- Treating whitespace as an identifier.
- Allowing environment values to override CLI values.

### Extension Challenge

Add `--format` with `text` and `json` choices.
