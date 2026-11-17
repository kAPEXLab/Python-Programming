# 09 - Charging Progress - Easy

## Question Details
- Concept: while loops
- Supporting concepts: Arithmetic, validation, termination conditions
- Difficulty: Easy
- Domain: Simulated EV charging
- Learning Objective: Use a while loop to advance a charging percentage until a target is reached.

## Scenario
A charging station simulation increases battery state of charge (SOC) in fixed percentage steps. No real charger or vehicle is used.

## Function Details
- Function signature: `charging_steps(start_soc: int, target_soc: int, step_percent: int) -> int`
- Behavior / return shape: Calculate how many charging steps are required to reach a target SOC.
- Exact accepted inputs: SOC values are integers from 0 through 100, with start at most target. Step is 1 through 100.
- Output and validation / behavior: Return the number of steps, including a final partial step if the increment would pass the target. If start equals target, return 0.

## Tasks to Implement
1. Implement `charging_steps` with the exact signature above and validate the inputs against these accepted rules: SOC values are integers from 0 through 100, with start at most target. Step is 1 through 100.
2. Calculate how many charging steps are required to reach a target SOC.
3. Implement this output contract exactly: Return the number of steps, including a final partial step if the increment would pass the target. If start equals target, return 0.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | charging_steps(0, 100, 30) | 4 | Typical valid input. |
| 2 | charging_steps(20, 20, 1) | 0 | Valid boundary case. |
| 3 | charging_steps(0, 1, 1) | 1 | Checks the rule at a threshold. |
| 4 | charging_steps(90, 100, 3) | 4 | Checks another valid input shape. |
| 5 | charging_steps(10, 95, 20) | 5 | Checks aggregate behavior. |

## Expected Deliverables
- Complete implementation of charging_steps that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Variables, arithmetic, functions, conditionals, and loops.

### Rules and Constraints
- Use a while loop.
- Never return a negative count.
- Raise ValueError for invalid input.

### Hints
1. Keep a current SOC and step counter.
2. Continue while current SOC is below target.
3. Cap the final SOC at the target.

### Common Mistakes
- Creating an infinite loop.
- Counting the initial state as a step.
- Rejecting a partial final increment.

### Extension Challenge
Return the SOC after every step as a list.
