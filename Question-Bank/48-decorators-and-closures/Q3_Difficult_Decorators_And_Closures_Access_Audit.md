# 48 - Auditing Decorated Diagnostic Access - Difficult

## Question Details
- **Concept:** Stateful decorators and closures
- **Supporting Python concepts:** Nonlocal state, authorization, metadata
- **Difficulty:** Difficult
- **Domain:** Offline diagnostic access audit
- **Learning Objective:** Track permitted and denied calls through a closure without global mutable state.

## Scenario
A simulated workshop API records how many diagnostic calls each decorated function receives.

## Function Details
- **Required Python interface:** Implement `audit_access(role: str) -> Callable` and decorate functions accepting `user: str`.
- **Behavior:** Allow roles `technician` and `engineer`; reject `guest` and any other unknown non-empty role with `PermissionError`. The decorator exposes `calls() -> int`, counting only permitted calls.
- **Return shape:** Return the wrapped result for permitted calls and maintain an isolated count per decorated function.
- **Input rules and constraints:** Role and user are non-empty strings; calls use keyword or positional user values. Additional constraints: Store the counter in a closure using `nonlocal`; Do not use a module-level counter; Access is simulated and cannot control a vehicle.

## Tasks to Implement
1. Implement the specified Python interface: Implement `audit_access(role: str) -> Callable` and decorate functions accepting `user: str`.
2. Apply the stated input validation and constraints: Role and user are non-empty strings; calls use keyword or positional user values.
3. Implement the required behavior: Allow roles `technician` and `engineer`; reject `guest` and any other unknown non-empty role with `PermissionError`. The decorator exposes `calls() -> int`, counting only permitted calls.
4. Return the specified result shape without changing the required ordering or formatting: Return the wrapped result for permitted calls and maintain an isolated count per decorated function.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `decorate lambda user: "OK:" + user with audit_access("technician"); call("A") then calls()` | `"OK:A"; calls() == 1` |
| 2 | `decorate lambda user: user.upper() with audit_access("engineer"); call("b") then calls()` | `"B"; calls() == 1` |
| 3 | `decorate lambda user: "seen:" + user with audit_access("technician"); call("C") twice` | `"seen:C" for each; calls() == 2` |
| 4 | `decorate lambda user: len(user) with audit_access("engineer"); call("diag")` | `4; calls() == 1` |
| 5 | `two separately decorated functions with role "technician"; call first once and second twice` | `first.calls() == 1; second.calls() == 2` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Decorators, closures, `nonlocal`, functions, and exceptions.

### Rules and Constraints

- Store the counter in a closure using `nonlocal`.
- Do not use a module-level counter.
- Access is simulated and cannot control a vehicle.

### Hints

Validate role when creating the decorator and increment only inside the authorized path.

### Common Mistakes

- Sharing state across decorated functions.
- Incrementing before authorization.
- Returning a mutable global counter.

### Extension Challenge

Expose separate permitted and denied counters.
