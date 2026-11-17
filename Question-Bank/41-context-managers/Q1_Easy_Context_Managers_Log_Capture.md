# 41 - Capturing Diagnostic Log Messages - Easy

## Question Details
- **Concept:** Context managers
- **Supporting Python concepts:** `__enter__`, `__exit__`, `io.StringIO`, exception propagation
- **Difficulty:** Easy
- **Domain:** Offline diagnostic log capture
- **Learning Objective:** Implement a context manager that captures simulated diagnostic messages and closes its resource correctly.

## Scenario
A test harness captures diagnostic text during a simulated scan without writing to a real vehicle interface.

## Function Details
- **Required Python interface:** Implement `LogCapture` with `__enter__`, `__exit__`, `write(message: str) -> None`, and `text() -> str`.
- **Behavior:** Capture messages separated by newlines. `text()` returns the captured text. The context manager must close its internal stream on exit and must not suppress exceptions.
- **Return shape:** Return exact captured text with one newline per write.
- **Input rules and constraints:** Messages must be strings. Empty messages are allowed and still produce a line. Additional constraints: Use `io.StringIO` internally; Writes after exit must raise `ValueError`; Do not connect to hardware or suppress exceptions.

## Tasks to Implement
1. Implement the specified Python interface: Implement `LogCapture` with `__enter__`, `__exit__`, `write(message: str) -> None`, and `text() -> str`.
2. Apply the stated input validation and constraints: Messages must be strings. Empty messages are allowed and still produce a line.
3. Implement the required behavior: Capture messages separated by newlines. `text()` returns the captured text. The context manager must close its internal stream on exit and must not suppress exceptions.
4. Return the specified result shape without changing the required ordering or formatting: Return exact captured text with one newline per write.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `with LogCapture() as capture: capture.write("start"); capture.text()` | `"start\n"` |
| 2 | `with LogCapture() as capture: capture.write("one"); capture.write("two"); capture.text()` | `"one\ntwo\n"` |
| 3 | `with LogCapture() as capture: capture.write(""); capture.text()` | `"\n"` |
| 4 | `with LogCapture() as capture: capture.text()` | `""` |
| 5 | `with LogCapture() as capture: capture.write("scan complete"); capture.text()` | `"scan complete\n"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Classes, context managers, strings, and exceptions.

### Rules and Constraints

- Use `io.StringIO` internally.
- Writes after exit must raise `ValueError`.
- Do not connect to hardware or suppress exceptions.

### Hints

Return `self` from `__enter__` and close in `__exit__`.

### Common Mistakes

- Suppressing exceptions by returning `True`.
- Forgetting to close the stream.
- Joining messages without a trailing newline.

### Extension Challenge

Add a maximum message count and raise `OverflowError` beyond it.
