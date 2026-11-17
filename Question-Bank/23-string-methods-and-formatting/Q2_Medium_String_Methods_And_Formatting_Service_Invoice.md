# 23 - String Methods and Formatting Service Invoice - Medium

## Question Details
- **Concept:** String methods and formatting
- **Supporting Python concepts:** Numeric formatting, validation, f-strings
- **Difficulty:** Medium
- **Domain:** Offline service invoice text
- **Learning Objective:** Format numeric service data into a stable, human-readable invoice line.
- **Estimated completion time:** 40 minutes

## Scenario
A workshop simulator needs one deterministic line for a labor item and its parts charge.

## Function Details
Implement `format_invoice_line(description: str, labor_hours: float, hourly_rate: float, parts_cost: float, tax_rate: float) -> str`.

**Required API / operation:** Calculate subtotal and tax, then format the invoice without currency ambiguity.

**Input rules and constraints:** Description must be non-empty after trimming. Labor hours, hourly rate, and parts cost are non-negative finite numbers. Tax rate is from 0 through 1 inclusive.

**Behavior and return shape:** Return `DESCRIPTION | subtotal=NN.NN | tax=NN.NN | total=NN.NN`, with all amounts rounded to two decimals and no currency symbols.

**Implementation rules:** Normalize description by trimming repeated internal whitespace to single spaces. Calculate subtotal as labor hours times hourly rate plus parts cost. Raise `ValueError` for invalid input.

## Tasks to Implement
1. Format numeric service data into a stable, human-readable invoice line.
2. Calculate subtotal and tax, then format the invoice without currency ambiguity.
3. Enforce all documented validation rules, including type, range, and structural constraints.
4. Return the exact type and shape documented above without mutating caller-owned inputs.

## Test Cases
All examples below are valid inputs; follow the stated operation to obtain the output.

| # | Valid input / operation | Exact expected output |
|---:|---|---|
| 1 | `description="Oil change", labor_hours=1, hourly_rate=50, parts_cost=10, tax_rate=0.1` | `'Oil change \| subtotal=60.00 \| tax=6.00 \| total=66.00'` |
| 2 | `description="  Tire   rotation ", labor_hours=0, hourly_rate=90, parts_cost=0, tax_rate=0` | `'Tire rotation \| subtotal=0.00 \| tax=0.00 \| total=0.00'` |
| 3 | `description="Battery", labor_hours=2, hourly_rate=75, parts_cost=25, tax_rate=0.08` | `'Battery \| subtotal=175.00 \| tax=14.00 \| total=189.00'` |
| 4 | `description="Inspection", labor_hours=0.5, hourly_rate=80, parts_cost=12.345, tax_rate=0.2` | `'Inspection \| subtotal=52.35 \| tax=10.47 \| total=62.81'` |
| 5 | `description="Service", labor_hours=1, hourly_rate=100, parts_cost=0, tax_rate=1` | `'Service \| subtotal=100.00 \| tax=100.00 \| total=200.00'` |

## Expected Deliverables
1. A complete Python implementation with the exact documented name, signature, and return shape.
2. A brief explanation of the approach, validation, and any important edge-case handling.
3. Test evidence showing the implementation's output for all five cases above.

## Additional Guidance

### Prerequisites
Strings, f-strings, floats, arithmetic, and exceptions.

### Rules and Constraints
- Normalize description by trimming repeated internal whitespace to single spaces.
- Calculate subtotal as labor hours times hourly rate plus parts cost.
- Raise `ValueError` for invalid input.

### Hints
1. Normalize the description with `split` and `join`.
2. Keep calculations numeric until final formatting.
3. Use two decimal places in each formatted amount.

### Common Mistakes
- Applying tax only to labor.
- Rounding subtotal before calculating tax.
- Leaving repeated spaces in the description.

### Extension Challenge
Return a multiline invoice with separate labor and parts lines while preserving exact rounding.
