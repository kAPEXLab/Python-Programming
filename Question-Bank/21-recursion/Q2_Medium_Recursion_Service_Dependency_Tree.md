# 21 - Recursion Service Dependency Tree - Medium

## Question Details
- **Concept:** Recursive tree search
- **Supporting Python concepts:** Lists, path tracking, validation, early results
- **Difficulty:** Medium
- **Domain:** Offline service dependency tree
- **Learning Objective:** Recursively find the first named service and return its path from the root.
- **Estimated completion time:** 40 minutes

## Scenario
A service plan models prerequisite jobs as a tree, with each node containing `service` and `dependencies`.

## Function Details
Implement `find_service_path(root: dict[str, object], target: str) -> list[str] | None`.

**Required API / operation:** Find a requested service and report the dependency path used to reach it.

**Input rules and constraints:** Service names are non-empty strings; target is non-empty. Each node has a `service` and a list of dependency nodes. Names are unique along any path and maximum depth is 100.

**Behavior and return shape:** Return the root-to-target service names as a list, or `None` if target is absent. Matching is case-insensitive after trimming; returned names preserve normalized title case.

**Implementation rules:** Use recursion to inspect dependencies. Stop searching a branch after finding a match. Raise `ValueError` for malformed trees or target; do not mutate input.

## Tasks to Implement
1. Recursively find the first named service and return its path from the root.
2. Find a requested service and report the dependency path used to reach it.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `root={'service': 'Engine', 'dependencies': []}, target='engine'` | `['Engine']` |
| 2 | `root={'service': 'Engine', 'dependencies': [{'service': 'Oil', 'dependencies': []}]}, target='oil'` | `['Engine', 'Oil']` |
| 3 | `root={'service': 'A', 'dependencies': [{'service': 'B', 'dependencies': []}]}, target='Missing'` | `None` |
| 4 | `root={'service': '  engine ', 'dependencies': [{'service': ' Filter ', 'dependencies': []}]}, target='filter'` | `['Engine', 'Filter']` |
| 5 | `root={'service': 'A', 'dependencies': [{'service': 'B', 'dependencies': [{'service': 'C', 'dependencies': []}]}]}, target='C'` | `['A', 'B', 'C']` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Recursion, nested dictionaries, strings, lists, and exceptions.

### Rules and Constraints
- Use recursion to inspect dependencies.
- Stop searching a branch after finding a match.
- Raise `ValueError` for malformed trees or target; do not mutate input.

### Hints
1. Put the current normalized service on the path.
2. Return immediately when it matches the target.
3. Copy the path when descending so sibling branches stay independent.

### Common Mistakes
- Returning only the target name.
- Sharing one mutable path across sibling branches.
- Continuing after a match.

### Extension Challenge
Return every matching path when duplicate service names are permitted.
