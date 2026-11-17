# 46 - Parsing Fleet Batch Job Arguments - Medium

## Question Details
- **Concept:** Subcommands and environment configuration
- **Supporting Python concepts:** `argparse`, choices, numeric parsing
- **Difficulty:** Medium
- **Domain:** Offline fleet batch job
- **Learning Objective:** Parse a fleet job command with a bounded batch size and configurable region.

## Scenario
A local batch job selects a fleet region and number of prerecorded records.

## Function Details
- **Required Python interface:** Implement `parse_job_args(argv: list[str], environ: Mapping[str, str]) -> dict[str, object]`.
- **Behavior:** Parse positional `region` from `north` or `south` and optional `--limit`; default limit comes from `FLEET_JOB_LIMIT` or 100. Return `{"region": ..., "limit": ...}`.
- **Return shape:** Return the validated dictionary.
- **Input rules and constraints:** Limit is an integer from 1 through 1000. Additional constraints: CLI `--limit` takes precedence over the environment; Translate `argparse` parse errors, including unknown or malformed arguments, into `ValueError`; Use `argparse` choices for regions; Operate on prerecorded fleet data only.

## Tasks to Implement
1. Implement the specified Python interface: Implement `parse_job_args(argv: list[str], environ: Mapping[str, str]) -> dict[str, object]`.
2. Apply the stated input validation and constraints: Limit is an integer from 1 through 1000.
3. Implement the required behavior: Parse positional `region` from `north` or `south` and optional `--limit`; default limit comes from `FLEET_JOB_LIMIT` or 100. Return `{"region": ..., "limit": ...}`.
4. Return the specified result shape without changing the required ordering or formatting: Return the validated dictionary.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `parse_job_args(["north"], {})` | `{"region": "north", "limit": 100}` |
| 2 | `parse_job_args(["south", "--limit", "1"], {})` | `{"region": "south", "limit": 1}` |
| 3 | `parse_job_args(["north"], {"FLEET_JOB_LIMIT": "250"})` | `{"region": "north", "limit": 250}` |
| 4 | `parse_job_args(["south", "--limit", "1000"], {"FLEET_JOB_LIMIT": "5"})` | `{"region": "south", "limit": 1000}` |
| 5 | `parse_job_args(["north", "--limit", "42"], {"FLEET_JOB_LIMIT": "99"})` | `{"region": "north", "limit": 42}` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Command-line parsing, dictionaries, type conversion, and validation.

### Rules and Constraints

- CLI `--limit` takes precedence over the environment.
- Translate `argparse` parse errors, including unknown or malformed arguments, into `ValueError`.
- Use `argparse` choices for regions.
- Operate on prerecorded fleet data only.

### Hints

Use `type=int` for the option, then apply environment fallback only when the option is absent.

### Common Mistakes

- Parsing all values as strings.
- Applying defaults before checking CLI values.
- Accepting unsupported regions.

### Extension Challenge

Add a `--dry-run` flag that returns a boolean.
