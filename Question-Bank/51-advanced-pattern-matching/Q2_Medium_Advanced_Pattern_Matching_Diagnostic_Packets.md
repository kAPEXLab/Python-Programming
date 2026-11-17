# 51 - Classifying Typed Diagnostic Packets - Medium

## Question Details
- **Concept:** Nested class and sequence patterns
- **Supporting Python concepts:** Dataclasses, guards, packet validation
- **Difficulty:** Medium
- **Domain:** Offline diagnostic packets
- **Learning Objective:** Use class and sequence patterns to classify typed diagnostic packet records.

## Scenario
A local analyzer receives synthetic packets represented by dataclasses and payload tuples.

## Function Details
- **Required Python interface:** Define `DiagnosticPacket(kind: str, payload: tuple[object, ...])` and implement `classify_packet(packet: DiagnosticPacket) -> str`.
- **Behavior:** Classify `"fault"` with one string code as `FAULT:<code>`, `"reading"` with one numeric value at least 0 as `READING`, and reject other shapes.
- **Return shape:** Return the exact classification or raise `ValueError` for invalid packets.
- **Input rules and constraints:** Packets use the stated dataclass and supported payload shapes. Additional constraints: Use class and sequence patterns; Do not mutate packet payloads; No real diagnostic bus is involved.

## Tasks to Implement
1. Implement the specified Python interface: Define `DiagnosticPacket(kind: str, payload: tuple[object, ...])` and implement `classify_packet(packet: DiagnosticPacket) -> str`.
2. Apply the stated input validation and constraints: Packets use the stated dataclass and supported payload shapes.
3. Implement the required behavior: Classify `"fault"` with one string code as `FAULT:<code>`, `"reading"` with one numeric value at least 0 as `READING`, and reject other shapes.
4. Return the specified result shape without changing the required ordering or formatting: Return the exact classification or raise `ValueError` for invalid packets.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `classify_packet(DiagnosticPacket("fault", ("P0420",)))` | `"FAULT:P0420"` |
| 2 | `classify_packet(DiagnosticPacket("reading", (0,)))` | `"READING"` |
| 3 | `classify_packet(DiagnosticPacket("reading", (12.5,)))` | `"READING"` |
| 4 | `classify_packet(DiagnosticPacket("fault", ("U0100",)))` | `"FAULT:U0100"` |
| 5 | `classify_packet(DiagnosticPacket("reading", (100,)))` | `"READING"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Dataclasses, tuples, `match-case`, and exception handling.

### Rules and Constraints

- Use class and sequence patterns.
- Do not mutate packet payloads.
- No real diagnostic bus is involved.

### Hints

Match the dataclass fields directly and nest tuple patterns in each case.

### Common Mistakes

- Accepting payloads with extra values.
- Matching only on `kind` and skipping payload validation.
- Converting all payloads to strings.

### Extension Challenge

Add a sequence packet that accepts exactly three numeric samples.
