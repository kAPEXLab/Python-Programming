# 50 - Registering Diagnostic Plugins with a Metaclass - Medium

## Question Details
- **Concept:** Metaclass registration
- **Supporting Python concepts:** Class creation, registries, abstract behavior
- **Difficulty:** Medium
- **Domain:** Offline diagnostic plugin registry
- **Learning Objective:** Register plugin subclasses automatically when their classes are created.

## Scenario
A local diagnostic toolkit discovers named plugins without loading external code.

## Function Details
- **Required Python interface:** Implement `PluginMeta(type)` and `PluginBase(metaclass=PluginMeta)` with `plugins() -> dict[str, type]`.
- **Behavior:** Register concrete subclasses by their non-empty `plugin_name` class attribute; exclude `PluginBase`. Reject duplicate names during class creation.
- **Return shape:** `plugins()` returns a copy of the registry mapping names to classes.
- **Input rules and constraints:** Plugins define `plugin_name: str` and a `run() -> str` method. Additional constraints: Registration belongs in the metaclass; Do not import plugins dynamically or connect to vehicles; Duplicate names raise `ValueError`.

## Tasks to Implement
1. Implement the specified Python interface: Implement `PluginMeta(type)` and `PluginBase(metaclass=PluginMeta)` with `plugins() -> dict[str, type]`.
2. Apply the stated input validation and constraints: Plugins define `plugin_name: str` and a `run() -> str` method.
3. Implement the required behavior: Register concrete subclasses by their non-empty `plugin_name` class attribute; exclude `PluginBase`. Reject duplicate names during class creation.
4. Return the specified result shape without changing the required ordering or formatting: `plugins()` returns a copy of the registry mapping names to classes.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `define PluginBase with registered subclasses Alpha(plugin_name="alpha") and Beta(plugin_name="beta"); sorted(PluginBase.plugins())` | `["alpha", "beta"]` |
| 2 | `Given Alpha is registered as in case 1: PluginBase.plugins()["alpha"].plugin_name` | `"alpha"` |
| 3 | `Given Beta is registered as in case 1: PluginBase.plugins()["beta"].plugin_name` | `"beta"` |
| 4 | `Given Alpha and Beta are registered as in case 1: names = PluginBase.plugins(); names.clear(); sorted(PluginBase.plugins())` | `["alpha", "beta"]` |
| 5 | `Define a fresh PluginBase with one registered subclass Reader(plugin_name="reader"); sorted(PluginBase.plugins())` | `["reader"]` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Classes, inheritance, metaclasses, dictionaries, and class attributes.

### Rules and Constraints

- Registration belongs in the metaclass.
- Do not import plugins dynamically or connect to vehicles.
- Duplicate names raise `ValueError`.

### Hints

Inspect the namespace during `__new__` and register only subclasses with a valid name.

### Common Mistakes

- Registering the base class.
- Returning the mutable internal dictionary.
- Detecting duplicates only when running a plugin.

### Extension Challenge

Add a `category` field and a lookup by category.
