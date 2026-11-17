# 35 - Evaluating Warranty Coverage - Medium

## Question Details
- **Concept:** Dataclasses and special methods
- **Supporting Python concepts:** Default fields, date arithmetic, validation, formatting
- **Difficulty:** Medium
- **Domain:** Offline warranty records
- **Learning Objective:** Model warranty data with dataclass defaults and a domain-specific special method.

## Scenario
A service archive needs deterministic warranty records that can report whether coverage applies on a date.

## Function Details
- **Required Python interface:** Define dataclass `WarrantyRecord` with `vehicle_id: str`, `start: date`, `months: int`, and `mileage_limit_km: int`. Implement `is_active(on_date: date, mileage_km: int) -> bool` and `label() -> str`.
- **Behavior:** Coverage includes the start date and ends on the last day before the month anniversary. Mileage is covered through the inclusive limit. Label format is `ID: YYYY-MM-DD for N months / M km`.
- **Return shape:** Return a boolean from `is_active` and the exact label format from `label`.
- **Input rules and constraints:** IDs are non-empty. Months are 1 through 120; mileage limit is non-negative; mileage is non-negative. Additional constraints: Store dates as `datetime.date`, not strings; Raise `ValueError` for invalid months or mileage; No current-date lookup; every date is supplied.

## Tasks to Implement
1. Implement the specified Python interface: Define dataclass `WarrantyRecord` with `vehicle_id: str`, `start: date`, `months: int`, and `mileage_limit_km: int`. Implement `is_active(on_date: date, mileage_km: int) -> bool` and `label() -> str`.
2. Apply the stated input validation and constraints: IDs are non-empty. Months are 1 through 120; mileage limit is non-negative; mileage is non-negative.
3. Implement the required behavior: Coverage includes the start date and ends on the last day before the month anniversary. Mileage is covered through the inclusive limit. Label format is `ID: YYYY-MM-DD for N months / M km`.
4. Return the specified result shape without changing the required ordering or formatting: Return a boolean from `is_active` and the exact label format from `label`.

## Test Cases

| # | Input / setup | Expected output |
|---:|---|---|
| 1 | `WarrantyRecord("EV-1", date(2024, 1, 15), 2, 20000), on_date=date(2024, 1, 15), mileage_km=0` | `True; label="EV-1: 2024-01-15 for 2 months / 20000 km"` |
| 2 | `WarrantyRecord("EV-2", date(2024, 1, 15), 2, 20000), on_date=date(2024, 3, 14), mileage_km=20000` | `True; label="EV-2: 2024-01-15 for 2 months / 20000 km"` |
| 3 | `WarrantyRecord("EV-2", date(2024, 1, 15), 2, 20000), on_date=date(2024, 3, 15), mileage_km=20000` | `False; label="EV-2: 2024-01-15 for 2 months / 20000 km"` |
| 4 | `WarrantyRecord("EV-3", date(2024, 5, 1), 12, 0), on_date=date(2024, 5, 1), mileage_km=0` | `True; label="EV-3: 2024-05-01 for 12 months / 0 km"` |
| 5 | `WarrantyRecord("EV-4", date(2024, 1, 1), 1, 5000), on_date=date(2024, 1, 31), mileage_km=5001` | `False; label="EV-4: 2024-01-01 for 1 months / 5000 km"` |

## Expected Deliverables
1. A complete Python implementation of the required interface.
2. A brief explanation of the design, validation, and Python concepts used.
3. Test evidence showing the five cases above and their expected outputs.

## Additional Requirements and Guidance

### Prerequisites

Dataclasses, `datetime.date`, methods, and comparisons.

### Rules and Constraints

- Store dates as `datetime.date`, not strings.
- Raise `ValueError` for invalid months or mileage.
- No current-date lookup; every date is supplied.

### Hints

Use calendar month arithmetic rather than approximating a month as 30 days.

### Common Mistakes

- Using today's date implicitly.
- Excluding the start date.
- Treating mileage limit as exclusive.

### Extension Challenge

Add a method that returns remaining months and kilometers.
