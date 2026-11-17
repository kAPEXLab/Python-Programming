# 01 - ECU Startup Sequence - Easy

## Question Details
- Concept: Input validation and multi-line f-string formatting
- Supporting concepts: Validation, logical reasoning, and clean function design
- Difficulty: Easy
- Domain: ECU startup and firmware boot diagnostics
- Learning Objective: Validate ECU identifiers and firmware labels, classify boot duration at 10 seconds, and return a three-line status report.

## Scenario
Implement a function named build_startup_report that validates the input values and returns a single multi-line string describing the ECU startup outcome.

## Function Details
- Function signature: `build_startup_report(ecu_name: str, firmware_version: str, boot_seconds: float) -> str`
- Behavior / return shape: Implement a function named build_startup_report that validates the input values and returns a single multi-line string describing the ECU startup outcome.
- Exact accepted inputs: ecu_name and firmware_version are non-empty strings; boot_seconds is a real number from 0 through 120 inclusive. Raise ValueError for invalid inputs.
- Output and validation / behavior: Return exactly three lines: ECU: <ecu_name>, Firmware: <firmware_version>, and Status: READY for boot_seconds <= 10 or SLOW_BOOT for boot_seconds > 10.

## Tasks to Implement
1. Implement `build_startup_report` with the exact signature above and validate the inputs against these accepted rules: ecu_name and firmware_version are non-empty strings; boot_seconds is a real number from 0 through 120 inclusive. Raise ValueError for invalid inputs.
2. Classify boot times of 10 seconds or less as `READY` and longer boot times as `SLOW_BOOT`, then assemble the report lines from the ECU name and firmware version.
3. Implement this output contract exactly: Return exactly three lines: ECU: <ecu_name>, Firmware: <firmware_version>, and Status: READY for boot_seconds <= 10 or SLOW_BOOT for boot_seconds > 10.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | build_startup_report("ECU-01", "v2.3", 4.5) | ECU: ECU-01<br>Firmware: v2.3<br>Status: READY | Nominal valid case under the 10s threshold. |
| 2 | build_startup_report("ECU-02", "v2.3", 10.0) | ECU: ECU-02<br>Firmware: v2.3<br>Status: READY | Boundary case at exactly 10.0 remains READY. |
| 3 | build_startup_report("ECU-03", "v2.3", 10.1) | ECU: ECU-03<br>Firmware: v2.3<br>Status: SLOW_BOOT | Just above the limit uses the slow-boot status. |
| 4 | build_startup_report("ECU-04", "v3.0-beta", 0) | ECU: ECU-04<br>Firmware: v3.0-beta<br>Status: READY | Zero-second startup is valid and ready. |
| 5 | build_startup_report("ECU-05", "v4.0", 120.0) | ECU: ECU-05<br>Firmware: v4.0<br>Status: SLOW_BOOT | Upper valid boundary is accepted and flagged as slow. |

## Expected Deliverables
- Complete implementation of build_startup_report that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.
