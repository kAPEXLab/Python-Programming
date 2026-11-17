# 45 - Loading Fleet Analytics Configuration - Easy

## Question Details
- **Concept:** Dependency and configuration boundaries
- **Supporting Python concepts:** `tomllib`, environment configuration, reproducibility
- **Difficulty:** Easy
- **Domain:** Offline fleet analytics
- **Learning Objective:** Read a small project configuration and use its declared rounding policy deterministically.

## Scenario
A fleet analytics tool reads a local TOML configuration rather than relying on machine-specific settings.

## Function Details
- **Required Python interface:** Implement `load_analytics_config(path: Path) -> dict[str, object]` using Python 3.12's `tomllib`.
- **Behavior:** Read `[analytics]` values `round_digits` and `unit`, requiring an integer 0 through 3 and unit `km` or `mi`.
- **Return shape:** Return the analytics dictionary with both validated values.
- **Input rules and constraints:** `path` identifies a UTF-8 TOML file with the required analytics table. Additional constraints: Use a virtual-environment-friendly standard-library implementation; Never hard-code a user's absolute path; Raise `ValueError` for invalid configuration.

## Tasks to Implement
1. Implement the specified Python interface: Implement `load_analytics_config(path: Path) -> dict[str, object]` using Python 3.12's `tomllib`.
2. Apply the stated input validation and constraints: `path` identifies a UTF-8 TOML file with the required analytics table.
3. Implement the required behavior: Read `[analytics]` values `round_digits` and `unit`, requiring an integer 0 through 3 and unit `km` or `mi`.
4. Return the specified result shape without changing the required ordering or formatting: Return the analytics dictionary with both validated values.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `load_analytics_config(Path("a.toml")) where [analytics] round_digits=0, unit="km"` | `{"round_digits": 0, "unit": "km"}` |
| 2 | `load_analytics_config(Path("b.toml")) where [analytics] round_digits=1, unit="mi"` | `{"round_digits": 1, "unit": "mi"}` |
| 3 | `load_analytics_config(Path("c.toml")) where [analytics] round_digits=2, unit="km"` | `{"round_digits": 2, "unit": "km"}` |
| 4 | `load_analytics_config(Path("d.toml")) where [analytics] round_digits=3, unit="mi"` | `{"round_digits": 3, "unit": "mi"}` |
| 5 | `load_analytics_config(Path("e.toml")) where [analytics] round_digits=2, unit="mi"` | `{"round_digits": 2, "unit": "mi"}` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Dictionaries, functions, file paths, TOML basics, and environment concepts.

### Rules and Constraints

- Use a virtual-environment-friendly standard-library implementation.
- Never hard-code a user's absolute path.
- Raise `ValueError` for invalid configuration.

### Hints

Parse with `tomllib.load` in binary mode and validate the resulting types.

### Common Mistakes

- Using `eval` to parse configuration.
- Accepting a boolean as an integer setting.
- Depending on the current working directory.

### Extension Challenge

Add a dependency version string and validate it against a simple policy.
