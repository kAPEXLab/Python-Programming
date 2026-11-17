# 45 - Building Layered Simulator Configuration - Difficult

## Question Details
- **Concept:** Layered configuration and reproducible environments
- **Supporting Python concepts:** `os.environ`, TOML, precedence, validation
- **Difficulty:** Difficult
- **Domain:** Offline vehicle simulator
- **Learning Objective:** Combine defaults, a TOML file, and environment variables with explicit precedence.

## Scenario
A simulator must produce the same setup from a checked-in config while allowing controlled test overrides.

## Function Details
- **Required Python interface:** Implement `build_simulator_config(path: Path, environ: Mapping[str, str]) -> dict[str, object]`.
- **Behavior:** Use defaults `speed_limit_kmh=120` and `mode="normal"`, then TOML `[simulator]`, then `SIM_SPEED_LIMIT_KMH` and `SIM_MODE`. Validate speed 0 through 300 and mode `normal` or `diagnostic`.
- **Return shape:** Return `{"speed_limit_kmh": int, "mode": str}` after applying precedence.
- **Input rules and constraints:** The path contains optional simulator settings; environment values are strings. Additional constraints: Do not read the process environment directly; use `environ`; Reject malformed or unknown mode values with `ValueError`; Simulation is offline and deterministic.

## Tasks to Implement
1. Implement the specified Python interface: Implement `build_simulator_config(path: Path, environ: Mapping[str, str]) -> dict[str, object]`.
2. Apply the stated input validation and constraints: The path contains optional simulator settings; environment values are strings.
3. Implement the required behavior: Use defaults `speed_limit_kmh=120` and `mode="normal"`, then TOML `[simulator]`, then `SIM_SPEED_LIMIT_KMH` and `SIM_MODE`. Validate speed 0 through 300 and mode `normal` or `diagnostic`.
4. Return the specified result shape without changing the required ordering or formatting: Return `{"speed_limit_kmh": int, "mode": str}` after applying precedence.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `build_simulator_config(Path("sim.toml"), {}) where file text is ""` | `{"speed_limit_kmh": 120, "mode": "normal"}` |
| 2 | `build_simulator_config(Path("sim.toml"), {}) where file text is "[simulator]\nspeed_limit_kmh = 80\nmode = \"diagnostic\"\n"` | `{"speed_limit_kmh": 80, "mode": "diagnostic"}` |
| 3 | `build_simulator_config(Path("sim.toml"), {"SIM_MODE": "diagnostic"}) where file text is "[simulator]\nspeed_limit_kmh = 100\nmode = \"normal\"\n"` | `{"speed_limit_kmh": 100, "mode": "diagnostic"}` |
| 4 | `build_simulator_config(Path("sim.toml"), {"SIM_SPEED_LIMIT_KMH": "0"}) where file text is ""` | `{"speed_limit_kmh": 0, "mode": "normal"}` |
| 5 | `build_simulator_config(Path("sim.toml"), {"SIM_SPEED_LIMIT_KMH": "300", "SIM_MODE": "diagnostic"}) where file text is "[simulator]\nspeed_limit_kmh = 90\nmode = \"normal\"\n"` | `{"speed_limit_kmh": 300, "mode": "diagnostic"}` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Dictionaries, TOML parsing, environment variables, classes, and exceptions.

### Rules and Constraints

- Do not read the process environment directly; use `environ`.
- Reject malformed or unknown mode values with `ValueError`.
- Simulation is offline and deterministic.

### Hints

Normalize each source into one dictionary, then validate only after precedence is resolved.

### Common Mistakes

- Letting a file override an environment variable.
- Parsing environment numbers as raw strings.
- Using ambient environment state in tests.

### Extension Challenge

Add a `battery_soc` setting with the same precedence rules.
