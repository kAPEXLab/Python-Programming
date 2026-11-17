# 33 - Abstraction and Abstract Base Classes Telemetry Sources - Medium

## Question Details
- **Concept:** Abstract base classes and interfaces
- **Supporting Python concepts:** Iterables, data validation, polymorphism, type hints
- **Difficulty:** Medium
- **Domain:** Offline telemetry source aggregation
- **Learning Objective:** Use an abstract source interface to aggregate normalized telemetry from different simulated sources.
- **Estimated completion time:** 60 minutes

## Scenario
A test harness combines battery and cabin telemetry from interchangeable offline sources.

## Function Details
Implement `merge_sources(sources: list[TelemetrySource]) -> dict[str, float]`. Each source must return finite numeric values. Later sources overwrite duplicate keys. Return keys in sorted order when displayed, but preserve a normal dictionary.

**Required API / operation:** Define abstract `TelemetrySource` with `read() -> dict[str, float]`. Implement `BatterySource` and `CabinSource`, initialized with a dictionary of values.

**Input rules and constraints:** At least one source is required. `BatterySource` supports `soc_percent`; `CabinSource` supports `temperature_c` and `soc_percent`. Values must be finite numbers, and source mappings may contain only keys supported by their source.

**Behavior and return shape:** Return one merged dictionary containing all source values.

**Implementation rules:** `TelemetrySource` cannot be instantiated directly. Read each source exactly once. Raise `ValueError` for an empty source list or invalid values.

## Tasks to Implement
1. Use an abstract source interface to aggregate normalized telemetry from different simulated sources.
2. Define abstract `TelemetrySource` with `read() -> dict[str, float]`. Implement `BatterySource` and `CabinSource`, initialized with a dictionary of values.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `merge_sources([BatterySource({'soc_percent': 50.0})])` | `{'soc_percent': 50.0}` |
| 2 | `merge_sources([CabinSource({'temperature_c': 21.5})])` | `{'temperature_c': 21.5}` |
| 3 | `merge_sources([BatterySource({'soc_percent': 50.0}), CabinSource({'temperature_c': 22.0, 'soc_percent': 60.0})])` | `{'soc_percent': 60.0, 'temperature_c': 22.0}` |
| 4 | `merge_sources([BatterySource({'soc_percent': 0.0})])` | `{'soc_percent': 0.0}` |
| 5 | `merge_sources([CabinSource({'temperature_c': -40.0, 'soc_percent': 100.0})])` | `{'soc_percent': 100.0, 'temperature_c': -40.0}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Abstract classes, lists, dictionaries, loops, and exceptions.

### Rules and Constraints
- `TelemetrySource` cannot be instantiated directly.
- Read each source exactly once.
- Raise `ValueError` for an empty source list or invalid values.

### Hints
Copy each returned mapping into the aggregate in source order.

### Common Mistakes
- Constructing the abstract source.
- Reading a source multiple times.
- Accepting `nan` as telemetry.

### Extension Challenge
Add a wheel-speed source that emits four named wheel values.
