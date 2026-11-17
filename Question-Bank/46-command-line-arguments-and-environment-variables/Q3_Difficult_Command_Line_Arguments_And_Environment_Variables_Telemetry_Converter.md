# 46 - Parsing Telemetry Converter Options - Difficult

## Question Details
- **Concept:** CLI configuration and environment validation
- **Supporting Python concepts:** `argparse`, enumerated choices, unit conversion
- **Difficulty:** Difficult
- **Domain:** Offline telemetry conversion
- **Learning Objective:** Build a deterministic converter whose source and target units are controlled by CLI arguments and environment defaults.

## Scenario
A telemetry converter transforms prerecorded speed samples for a report.

## Function Details
- **Required Python interface:** Implement `parse_converter_args(argv: list[str], environ: Mapping[str, str]) -> dict[str, str]`.
- **Behavior:** Parse `--source` and `--target`, each `kmh` or `mph`; defaults are `TELEMETRY_SOURCE` or `kmh`, and `TELEMETRY_TARGET` or `mph`.
- **Return shape:** Return `{"source": normalized_source, "target": normalized_target}`.
- **Input rules and constraints:** All unit names are case-insensitive after stripping whitespace. Additional constraints: CLI options override environment values; Translate `argparse` parse errors, including unknown or malformed arguments, into `ValueError`; Reject missing, blank, or unsupported units with `ValueError`; Do not read live telemetry.

## Tasks to Implement
1. Implement the specified Python interface: Implement `parse_converter_args(argv: list[str], environ: Mapping[str, str]) -> dict[str, str]`.
2. Apply the stated input validation and constraints: All unit names are case-insensitive after stripping whitespace.
3. Implement the required behavior: Parse `--source` and `--target`, each `kmh` or `mph`; defaults are `TELEMETRY_SOURCE` or `kmh`, and `TELEMETRY_TARGET` or `mph`.
4. Return the specified result shape without changing the required ordering or formatting: Return `{"source": normalized_source, "target": normalized_target}`.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `parse_converter_args([], {})` | `{"source": "kmh", "target": "mph"}` |
| 2 | `parse_converter_args(["--source", "mph"], {})` | `{"source": "mph", "target": "mph"}` |
| 3 | `parse_converter_args([], {"TELEMETRY_SOURCE": "MPH", "TELEMETRY_TARGET": "KMH"})` | `{"source": "mph", "target": "kmh"}` |
| 4 | `parse_converter_args(["--source", " KMH ", "--target", " mph "], {})` | `{"source": "kmh", "target": "mph"}` |
| 5 | `parse_converter_args(["--target", "kmh"], {"TELEMETRY_SOURCE": "mph"})` | `{"source": "mph", "target": "kmh"}` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

`argparse`, mappings, numeric conversion, environment variables, and exceptions.

### Rules and Constraints

- CLI options override environment values.
- Translate `argparse` parse errors, including unknown or malformed arguments, into `ValueError`.
- Reject missing, blank, or unsupported units with `ValueError`.
- Do not read live telemetry.

### Hints

Normalize source values through one helper and validate before constructing the result.

### Common Mistakes

- Accepting `kph` as an undocumented alias.
- Mixing conversion with argument parsing.
- Letting environment values win over CLI values.

### Extension Challenge

Add `--precision` with an integer range of 0 through 3.
