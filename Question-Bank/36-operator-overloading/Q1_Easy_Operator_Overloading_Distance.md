# 36 - Distance Value Arithmetic - Easy

## Question Details
- **Concept:** Operator overloading
- **Supporting Python concepts:** Immutable value objects, comparisons, numeric validation, formatting
- **Difficulty:** Easy
- **Domain:** Offline trip distance arithmetic
- **Learning Objective:** Implement safe arithmetic and comparisons for a distance value object.

## Scenario
A trip simulator needs distances that cannot be accidentally combined with unrelated units.

## Function Details
- **Required Python interface:** Implement `Distance(km: float)` with `__add__`, `__sub__`, `__lt__`, `__eq__`, and `__str__`.
- **Behavior:** Distance arithmetic must return new `Distance` objects. Subtraction may not produce a negative result. String output is `NN.N km` with one decimal place.
- **Return shape:** Return value objects for arithmetic, booleans for comparisons, and formatted text for `str`.
- **Input rules and constraints:** Kilometers must be finite and non-negative. Arithmetic operands must also be `Distance` objects. Additional constraints: Do not mutate either operand; Return `NotImplemented` for unrelated operand types; Raise `ValueError` for negative results or invalid construction.

## Tasks to Implement
1. Implement the specified Python interface: Implement `Distance(km: float)` with `__add__`, `__sub__`, `__lt__`, `__eq__`, and `__str__`.
2. Apply the stated input validation and constraints: Kilometers must be finite and non-negative. Arithmetic operands must also be `Distance` objects.
3. Implement the required behavior: Distance arithmetic must return new `Distance` objects. Subtraction may not produce a negative result. String output is `NN.N km` with one decimal place.
4. Return the specified result shape without changing the required ordering or formatting: Return value objects for arithmetic, booleans for comparisons, and formatted text for `str`.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `Distance(12.5) + Distance(7.5); result.km` | `20.0` |
| 2 | `Distance(10.0) - Distance(4.25); result.km` | `5.75` |
| 3 | `str(Distance(0.0))` | `"0.0 km"` |
| 4 | `Distance(5.0) < Distance(6.0)` | `True` |
| 5 | `Distance(5.0) == Distance(5.0)` | `True` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Classes, special methods, numeric operators, and exceptions.

### Rules and Constraints

- Do not mutate either operand.
- Return `NotImplemented` for unrelated operand types.
- Raise `ValueError` for negative results or invalid construction.

### Hints

Validate in the constructor and delegate operand validation in each operator.

### Common Mistakes

- Mutating the left operand.
- Comparing raw numbers silently.
- Rounding stored values instead of display values.

### Extension Challenge

Add multiplication by a non-negative numeric route count.
