# 50 - Collecting Validated Configuration Fields - Difficult

## Question Details
- **Concept:** Descriptor and metaclass cooperation
- **Supporting Python concepts:** Field collection, class creation, validation
- **Difficulty:** Difficult
- **Domain:** Offline vehicle configuration
- **Learning Objective:** Collect descriptor-defined configuration fields while validating assignments on instances.

## Scenario
A simulator configuration class declares bounded fields that should be discoverable and validated uniformly.

## Function Details
- **Required Python interface:** Implement `ConfigField(value_type: type, default: object)` and `ConfigMeta(type)` with `field_names() -> tuple[str, ...]`.
- **Behavior:** Collect fields in declaration order, expose defaults, and reject assignments of the wrong type. `VehicleConfig` declares `speed_limit: int = ConfigField(int, 120)` and `mode: str = ConfigField(str, "normal")`; speed must be from 0 through 300 and mode must be `normal` or `diagnostic`.
- **Return shape:** Instances expose validated attributes; `field_names()` returns `("speed_limit", "mode")`.
- **Input rules and constraints:** Speed limit is an integer 0 through 300; mode is `normal` or `diagnostic`. Additional constraints: Descriptors store per-instance values; Validate speed values in the inclusive range 0 through 300 and mode values as `normal` or `diagnostic`; Metaclass collection must include inherited fields; Configuration is synthetic and offline.

## Tasks to Implement
1. Implement the specified Python interface: Implement `ConfigField(value_type: type, default: object)` and `ConfigMeta(type)` with `field_names() -> tuple[str, ...]`.
2. Apply the stated input validation and constraints: Speed limit is an integer 0 through 300; mode is `normal` or `diagnostic`.
3. Implement the required behavior: Collect fields in declaration order, expose defaults, and reject assignments of the wrong type. `VehicleConfig` declares `speed_limit: int = ConfigField(int, 120)` and `mode: str = ConfigField(str, "normal")`; speed must be from 0 through 300 and mode must be `normal` or `diagnostic`.
4. Return the specified result shape without changing the required ordering or formatting: Instances expose validated attributes; `field_names()` returns `("speed_limit", "mode")`.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `VehicleConfig().speed_limit` | `120` |
| 2 | `VehicleConfig().mode` | `"normal"` |
| 3 | `config.speed_limit = 0; config.speed_limit` | `0` |
| 4 | `config.mode = "diagnostic"; config.mode` | `"diagnostic"` |
| 5 | `VehicleConfig.field_names()` | `("speed_limit", "mode")` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Descriptors, metaclasses, inheritance, mappings, and exceptions.

### Rules and Constraints

- Descriptors store per-instance values.
- Validate speed values in the inclusive range 0 through 300 and mode values as `normal` or `diagnostic`.
- Metaclass collection must include inherited fields.
- Configuration is synthetic and offline.

### Hints

Let `__set_name__` capture field names and have the metaclass inspect descriptor instances.

### Common Mistakes

- Sharing values between configuration instances.
- Collecting fields alphabetically instead of declaration order.
- Validating only during serialization.

### Extension Challenge

Add serialization to a plain dictionary while omitting unset optional fields.
