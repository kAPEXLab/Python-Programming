# 10 - Invalid Packets - Medium

## Question Details
- Concept: continue and break
- Supporting concepts: Validation, filtering, aggregation, dictionaries
- Difficulty: Medium
- Domain: Simulated telemetry packet processing
- Learning Objective: Skip malformed packets with continue and stop processing at an end marker with break.

## Scenario
A simulated telemetry stream contains packets with type and value. A packet with type END ends the stream. Invalid packets are skipped.

## Function Details
- Function signature: `process_packets(packets: list[dict[str, object]]) -> dict[str, object]`
- Behavior / return shape: Sum valid SPEED packet values before the first end marker and count skipped packets.
- Exact accepted inputs: Each item should be a dictionary. Valid speed packets have `type="SPEED"` and numeric `value` from 0 through 300. `END` requires no value. Other packet types are invalid and skipped. The stream may contain 0 to 10,000 items.
- Output and validation / behavior: Sum valid speeds without rounding and count them. Count malformed or irrelevant packets before `END` as skipped. Ignore all packets after `END`.

## Tasks to Implement
1. Implement `process_packets` with the exact signature above and validate the inputs against these accepted rules: Each item should be a dictionary. Valid speed packets have `type="SPEED"` and numeric `value` from 0 through 300. `END` requires no value. Other packet types are invalid and skipped. The stream may contain 0 to 10,000 items.
2. Sum valid SPEED packet values before the first end marker and count skipped packets.
3. Return exactly the specified result: Sum valid speeds without rounding and count them. Count malformed or irrelevant packets before `END` as skipped. Ignore all packets after `END`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | process_packets([{"type": "SPEED", "value": 50}]) | {"speed_total_kmh": 50, "valid_speed_count": 1, "skipped_count": 0} | Typical valid input. |
| 2 | process_packets([{"type": "SPEED", "value": 0}, {"type": "END"}]) | {"speed_total_kmh": 0, "valid_speed_count": 1, "skipped_count": 0} | Valid boundary case. |
| 3 | process_packets([{"type": "NOISE"}, {"type": "SPEED", "value": 300}]) | {"speed_total_kmh": 300, "valid_speed_count": 1, "skipped_count": 1} | Checks the threshold rule. |
| 4 | process_packets([{"type": "SPEED", "value": 20}, {"type": "END"}, {"type": "SPEED", "value": 100}]) | {"speed_total_kmh": 20, "valid_speed_count": 1, "skipped_count": 0} | Checks an alternate valid shape. |
| 5 | process_packets([]) | {"speed_total_kmh": 0, "valid_speed_count": 0, "skipped_count": 0} | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of process_packets that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Lists, dictionaries, loops, conditionals, functions, and exceptions.

### Rules and Constraints
- Use continue for skipped packets and break for END.
- Do not raise for a malformed packet; skip it.
- Do not mutate input.

### Hints
1. Check for END before validating ordinary packets.
2. Increment skipped count before continue.
3. Validate speed ranges before aggregation.

### Common Mistakes
- Processing data after END.
- Raising instead of skipping malformed packets.
- Counting END as skipped.

### Extension Challenge
Track valid TEMPERATURE packets in a second aggregate.
