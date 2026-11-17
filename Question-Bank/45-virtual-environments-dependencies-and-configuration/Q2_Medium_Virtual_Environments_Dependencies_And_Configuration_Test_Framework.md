# 45 - Checking an Installed Dependency Version - Medium

## Question Details
- **Concept:** Dependency pinning and environment configuration
- **Supporting Python concepts:** `importlib.metadata`, semantic version checks, virtual environments
- **Difficulty:** Medium
- **Domain:** Offline test framework setup
- **Learning Objective:** Verify that an installed test dependency satisfies a deterministic minimum version.

## Scenario
A simulated test framework refuses to run when its required local dependency is too old.

## Function Details
- **Required Python interface:** Implement `require_version(package: str, minimum: tuple[int, int]) -> str` using `importlib.metadata.version`.
- **Behavior:** Parse the package's major and minor version, return `READY:<package>:<version>` when sufficient, and raise `RuntimeError` when missing or too old.
- **Return shape:** Return the exact readiness string for a satisfied dependency.
- **Input rules and constraints:** `package` is a non-empty distribution name; test doubles may provide versions like `2.4.1`. Additional constraints: Do not install packages from code; Treat missing metadata as a framework error; Compare major and minor components numerically.

## Tasks to Implement
1. Implement the specified Python interface: Implement `require_version(package: str, minimum: tuple[int, int]) -> str` using `importlib.metadata.version`.
2. Apply the stated input validation and constraints: `package` is a non-empty distribution name; test doubles may provide versions like `2.4.1`.
3. Implement the required behavior: Parse the package's major and minor version, return `READY:<package>:<version>` when sufficient, and raise `RuntimeError` when missing or too old.
4. Return the specified result shape without changing the required ordering or formatting: Return the exact readiness string for a satisfied dependency.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `require_version("sample-lib", (1, 0)); metadata.version returns "1.0.0"` | `"READY:sample-lib:1.0.0"` |
| 2 | `require_version("sample-lib", (2, 4)); metadata.version returns "2.4.1"` | `"READY:sample-lib:2.4.1"` |
| 3 | `require_version("sample-lib", (2, 4)); metadata.version returns "2.10.0"` | `"READY:sample-lib:2.10.0"` |
| 4 | `require_version("sample-lib", (3, 0)); metadata.version returns "3.0"` | `"READY:sample-lib:3.0"` |
| 5 | `require_version("sample-lib", (0, 9)); metadata.version returns "1.2.3"` | `"READY:sample-lib:1.2.3"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Functions, exceptions, package metadata, version strings, and virtual environments.

### Rules and Constraints

- Do not install packages from code.
- Treat missing metadata as a framework error.
- Compare major and minor components numerically.

### Hints

Patch or inject metadata lookup in tests rather than requiring a real installation.

### Common Mistakes

- Comparing version strings lexicographically.
- Installing packages as a side effect.
- Ignoring missing package metadata.

### Extension Challenge

Support a maximum compatible major version from configuration.
