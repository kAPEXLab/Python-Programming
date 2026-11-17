# 47 - Streaming Matching Diagnostic Log Lines - Medium

## Question Details
- **Concept:** Generator functions
- **Supporting Python concepts:** Lazy file iteration, `yield`, filtering
- **Difficulty:** Medium
- **Domain:** Offline large diagnostic log
- **Learning Objective:** Stream matching diagnostic lines without loading a complete log into memory.

## Scenario
A large prerecorded log must expose only lines containing a requested diagnostic code.

## Function Details
- **Required Python interface:** Implement `matching_lines(lines: Iterable[str], code: str) -> Iterator[str]`.
- **Behavior:** Yield stripped lines containing the exact case-sensitive `code`, in original order. Reject a blank code.
- **Return shape:** Yield matching stripped strings lazily.
- **Input rules and constraints:** `lines` is any iterable of text lines; `code` is a non-empty string. Additional constraints: Use `yield`; do not return a list; Preserve duplicate matches and order; Input is prerecorded and contains no proprietary data.

## Tasks to Implement
1. Implement the specified Python interface: Implement `matching_lines(lines: Iterable[str], code: str) -> Iterator[str]`.
2. Apply the stated input validation and constraints: `lines` is any iterable of text lines; `code` is a non-empty string.
3. Implement the required behavior: Yield stripped lines containing the exact case-sensitive `code`, in original order. Reject a blank code.
4. Return the specified result shape without changing the required ordering or formatting: Yield matching stripped strings lazily.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `list(matching_lines(["P0420 detected\n", "ok\n"], "P0420"))` | `["P0420 detected"]` |
| 2 | `list(matching_lines(iter(["x P1", "P1", "P10"]), "P1"))` | `["x P1", "P1", "P10"]` |
| 3 | `list(matching_lines(["fault\n", "fault\n"], "fault"))` | `["fault", "fault"]` |
| 4 | `list(matching_lines(["p0420", "P0420"], "P0420"))` | `["P0420"]` |
| 5 | `list(matching_lines([], "U0100"))` | `[]` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Generators, strings, file-like objects, and loops.

### Rules and Constraints

- Use `yield`; do not return a list.
- Preserve duplicate matches and order.
- Input is prerecorded and contains no proprietary data.

### Hints

Strip each line immediately before checking and yielding it.

### Common Mistakes

- Reading all lines into a list first.
- Using substring normalization that changes case behavior.
- Dropping duplicate events.

### Extension Challenge

Yield `(line_number, line)` pairs while remaining lazy.
