# 21 - Recursion Component Hierarchy - Easy

## Question Details
- **Concept:** Recursive traversal
- **Supporting Python concepts:** Nested dictionaries, base cases, validation, counting
- **Difficulty:** Easy
- **Domain:** Simulated component hierarchy
- **Learning Objective:** Use recursion to count every node in a nested component hierarchy.
- **Estimated completion time:** 30 minutes

## Scenario
An offline vehicle fixture represents components as nodes with a name and child nodes.

## Function Details
Implement `count_components(node: dict[str, object]) -> int`.

**Required API / operation:** Count the current component and every descendant.

**Input rules and constraints:** Each node has a non-empty string `name` and a `children` list of zero or more valid nodes. Maximum depth is 100.

**Behavior and return shape:** Return the total number of nodes, including the root.

**Implementation rules:** Use a base case for a node with no children. Use recursion for every child node. Reject malformed nodes with `ValueError` and do not mutate input.

## Tasks to Implement
1. Use recursion to count every node in a nested component hierarchy.
2. Count the current component and every descendant.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `node={'name': 'root', 'children': []}` | `1` |
| 2 | `node={'name': 'root', 'children': [{'name': 'A', 'children': []}]}` | `2` |
| 3 | `node={'name': 'root', 'children': [{'name': 'A', 'children': []}, {'name': 'B', 'children': []}]}` | `3` |
| 4 | `node={'name': 'r', 'children': [{'name': 'a', 'children': [{'name': 'x', 'children': []}]}]}` | `3` |
| 5 | `node={'name': 'r', 'children': [{'name': 'a', 'children': []}, {'name': 'b', 'children': [{'name': 'c', 'children': []}]}]}` | `4` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Functions, dictionaries, lists, conditionals, and validation.

### Rules and Constraints
- Use a base case for a node with no children.
- Use recursion for every child node.
- Reject malformed nodes with `ValueError` and do not mutate input.

### Hints
1. Count the current node once.
2. Add recursive counts for each child.
3. Validate before descending.

### Common Mistakes
- Returning zero for a leaf.
- Counting only direct children.
- Forgetting malformed nested nodes.

### Extension Challenge
Return the maximum hierarchy depth as well as the node count.
