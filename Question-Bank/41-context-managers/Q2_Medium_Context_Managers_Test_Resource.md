# 41 - Managing a Simulated Test Resource - Medium

## Question Details
- **Concept:** Context managers
- **Supporting Python concepts:** Resource lifecycle, state flags, exception propagation, testing
- **Difficulty:** Medium
- **Domain:** Offline test-resource reservation
- **Learning Objective:** Guarantee acquisition and release of a simulated test resource through a context manager.

## Scenario
A test harness reserves a named resource for one simulated test at a time.

## Function Details
- **Required Python interface:** Implement `TestResource(name: str)` with `__enter__`, `__exit__`, `use(label: str) -> str`, and `released: bool`.
- **Behavior:** Entering marks the resource active; `use` returns `name:label`; exiting marks it released. Use outside the context raises `RuntimeError`. Do not suppress body exceptions.
- **Return shape:** Return the exact `name:label` string from valid use.
- **Input rules and constraints:** Name and label are non-empty strings. A resource starts unreleased and inactive. Additional constraints: Release must happen even when the body raises; A resource cannot be entered twice without a matching exit; This resource is entirely simulated.

## Tasks to Implement
1. Implement the specified Python interface: Implement `TestResource(name: str)` with `__enter__`, `__exit__`, `use(label: str) -> str`, and `released: bool`.
2. Apply the stated input validation and constraints: Name and label are non-empty strings. A resource starts unreleased and inactive.
3. Implement the required behavior: Entering marks the resource active; `use` returns `name:label`; exiting marks it released. Use outside the context raises `RuntimeError`. Do not suppress body exceptions.
4. Return the specified result shape without changing the required ordering or formatting: Return the exact `name:label` string from valid use.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `with TestResource("dyno") as resource: result = resource.use("run-1"); inspect resource.released after exit` | `("dyno:run-1", True)` |
| 2 | `with TestResource("logger") as resource: result = resource.use("capture"); inspect resource.released after exit` | `("logger:capture", True)` |
| 3 | `with TestResource("battery-sim") as resource: result = resource.use("check"); inspect resource.released after exit` | `("battery-sim:check", True)` |
| 4 | `with TestResource("fixture-1") as resource: result = resource.use("idle"); inspect resource.released after exit` | `("fixture-1:idle", True)` |
| 5 | `with TestResource("bench") as resource: result = resource.use("test-5"); inspect resource.released after exit` | `("bench:test-5", True)` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Classes, `with`, methods, state validation, and exceptions.

### Rules and Constraints

- Release must happen even when the body raises.
- A resource cannot be entered twice without a matching exit.
- This resource is entirely simulated.

### Hints

Track active and released state separately; cleanup belongs in `__exit__`.

### Common Mistakes

- Releasing only on successful exit.
- Returning `True` from `__exit__`.
- Allowing use before acquisition.

### Extension Challenge

Add an acquisition counter for repeated sequential uses.
