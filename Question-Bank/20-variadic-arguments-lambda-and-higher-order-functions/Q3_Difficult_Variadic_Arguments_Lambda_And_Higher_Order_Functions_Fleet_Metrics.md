# 20 - Variadic Arguments Lambda and Higher Order Functions Fleet Metrics - Difficult

## Question Details
- **Concept:** Variadic arguments and function composition
- **Supporting Python concepts:** Higher-order functions, lambdas, reducers, validation
- **Difficulty:** Difficult
- **Domain:** Simulated fleet metrics pipeline
- **Learning Objective:** Compose a variable number of metric functions and apply them to validated fleet values.
- **Estimated completion time:** 55 minutes

## Scenario
An offline fleet tool receives numeric distances and lets callers choose metric functions.

## Function Details
Implement `apply_fleet_metrics(readings: list[float], *metrics: tuple[str, typing.Callable[[list[float]], float]]) -> dict[str, float]`.

**Required API / operation:** Apply each supplied metric function to the same readings and return results by function name.

**Input rules and constraints:** Readings are 0 through 1000 finite kilometers, with at least one item. Each metric is `(name, function)`, names are unique non-empty strings, and functions accept `list[float]` and return finite numbers. Non-numeric or non-finite readings and metric results raise `ValueError`.

**Behavior and return shape:** Call each metric in input order and return a dictionary mapping names to results rounded to two decimals. A metric exception must propagate unchanged.

**Implementation rules:** Use higher-order calls; do not identify functions by name with conditionals. Do not mutate readings or metric tuples. Reject malformed inputs with `ValueError`.

## Tasks to Implement
1. Compose a variable number of metric functions and apply them to validated fleet values.
2. Apply each supplied metric function to the same readings and return results by function name.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `readings=[1.0], metrics=(('sum', sum),)` | `{'sum': 1.0}` |
| 2 | `readings=[1.0, 2.0, 3.0], metrics=(('mean', lambda xs: sum(xs)/len(xs)),)` | `{'mean': 2.0}` |
| 3 | `readings=[0.0, 1000.0], metrics=(('maximum', max), ('minimum', min))` | `{'maximum': 1000.0, 'minimum': 0.0}` |
| 4 | `readings=[1.25, 2.25], metrics=(('total', sum), ('count', lambda xs: len(xs) * 1.0))` | `{'total': 3.5, 'count': 2.0}` |
| 5 | `readings=[10], metrics=(('first', lambda xs: xs[0]),)` | `{'first': 10.0}` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, `*args`, lambdas, callable values, lists, and exceptions.

### Rules and Constraints
- Use higher-order calls; do not identify functions by name with conditionals.
- Do not mutate readings or metric tuples.
- Reject malformed inputs with `ValueError`.

### Hints
1. Validate callable objects with `callable()`.
2. Store each returned metric under its supplied name.
3. Round only after the callable returns.

### Common Mistakes
- Calling every function with one reading instead of the full list.
- Silently swallowing callable exceptions.
- Overwriting duplicate metric names.

### Extension Challenge
Accept a callable that receives the prior result and the next metric result to build a pipeline summary.
