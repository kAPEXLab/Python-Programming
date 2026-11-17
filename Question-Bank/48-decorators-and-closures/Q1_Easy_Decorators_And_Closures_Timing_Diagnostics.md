# 48 - Timing Diagnostic Functions - Easy

## Question Details
- **Concept:** Function decorators
- **Supporting Python concepts:** Closures, `functools.wraps`, return values
- **Difficulty:** Easy
- **Domain:** Offline diagnostic timing
- **Learning Objective:** Wrap a diagnostic function while preserving its metadata and result.

## Scenario
A local diagnostic harness records elapsed time around a simulated check.

## Function Details
- **Required Python interface:** Implement `timed_check(func: Callable[..., T]) -> Callable[..., tuple[T, float]]`.
- **Behavior:** Return a decorated function that returns `(original_result, elapsed_seconds)` and preserves `__name__` and `__doc__`.
- **Return shape:** Elapsed time is a non-negative float from the supplied clock.
- **Input rules and constraints:** The wrapped callable accepts arbitrary positional and keyword arguments. Additional constraints: Use a closure and `functools.wraps`; Do not alter the original result; Timing is local simulation only.

## Tasks to Implement
1. Implement the specified Python interface: Implement `timed_check(func: Callable[..., T]) -> Callable[..., tuple[T, float]]`.
2. Apply the stated input validation and constraints: The wrapped callable accepts arbitrary positional and keyword arguments.
3. Implement the required behavior: Return a decorated function that returns `(original_result, elapsed_seconds)` and preserves `__name__` and `__doc__`.
4. Return the specified result shape without changing the required ordering or formatting: Elapsed time is a non-negative float from the supplied clock.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `@timed_check with perf_counter patched to return 12.0 then 12.25; wrapped function returns "OK"` | `("OK", 0.25)` |
| 2 | `@timed_check with perf_counter patched to return 0.0 then 1.5; wrapped function returns 7` | `(7, 1.5)` |
| 3 | `@timed_check with perf_counter patched to return 5.0 twice; wrapped function returns None` | `(None, 0.0)` |
| 4 | `@timed_check with perf_counter patched to return 2.0 then 2.125; wrapped function returns (1, 2)` | `((1, 2), 0.125)` |
| 5 | `@timed_check with perf_counter patched to return 9.0 then 10.0; wrapped function returns True` | `(True, 1.0)` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Functions, nested functions, decorators, and `time.perf_counter`.

### Rules and Constraints

- Use a closure and `functools.wraps`.
- Do not alter the original result.
- Timing is local simulation only.

### Hints

Capture the clock before and after calling the function, then subtract.

### Common Mistakes

- Swallowing wrapped exceptions.
- Returning only elapsed time.
- Omitting `functools.wraps`.

### Extension Challenge

Add a logger callback that receives the function name and elapsed time.
