# 44 - Running a Supplied Unit Test Suite - Difficult

## Question Details
- **Concept:** `unittest` and executable module guards
- **Supporting Python concepts:** Test discovery, `unittest.mock`, exit status
- **Difficulty:** Difficult
- **Domain:** Offline diagnostic test runner
- **Learning Objective:** Create a small standard-library test runner that can be imported without starting tests.

## Scenario
A diagnostic team needs a deterministic runner for a local suite of simulated checks.

## Function Details
- **Required Python interface:** Implement `run_checks(loader: unittest.TestLoader, runner: unittest.TestRunner, suite: unittest.TestSuite) -> bool`.
- **Behavior:** Run the supplied suite and return `True` only when the result is successful. Do not call discovery or execute tests at import time.
- **Return shape:** Return a boolean success value and leave test output to the supplied runner.
- **Input rules and constraints:** The loader, runner, and suite are standard `unittest` objects or compatible test doubles. Additional constraints: Use `unittest` from the standard library; Keep the entry point under `if __name__ == "__main__"`; Tests are local simulations only.

## Tasks to Implement
1. Implement the specified Python interface: Implement `run_checks(loader: unittest.TestLoader, runner: unittest.TestRunner, suite: unittest.TestSuite) -> bool`.
2. Apply the stated input validation and constraints: The loader, runner, and suite are standard `unittest` objects or compatible test doubles.
3. Implement the required behavior: Run the supplied suite and return `True` only when the result is successful. Do not call discovery or execute tests at import time.
4. Return the specified result shape without changing the required ordering or formatting: Return a boolean success value and leave test output to the supplied runner.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `run_checks(loader, runner whose run(suite) result has wasSuccessful() == True, suite)` | `True` |
| 2 | `run_checks(loader, runner whose run(suite) result has wasSuccessful() == False, suite)` | `False` |
| 3 | `run_checks(loader, runner whose wasSuccessful() returns True for an empty suite, suite)` | `True` |
| 4 | `run_checks(loader, runner whose wasSuccessful() returns False after one error, suite)` | `False` |
| 5 | `run_checks(loader, runner whose wasSuccessful() returns True with one skipped test, suite)` | `True` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Classes, functions, `unittest`, mocks, and the main guard.

### Rules and Constraints

- Use `unittest` from the standard library.
- Keep the entry point under `if __name__ == "__main__"`.
- Tests are local simulations only.

### Hints

Call `runner.run(suite)` once and inspect only `wasSuccessful()`.

### Common Mistakes

- Returning the result object instead of a boolean.
- Running tests while importing the module.
- Rebuilding a caller-supplied suite.

### Extension Challenge

Add a command-line switch that selects one named test suite.
