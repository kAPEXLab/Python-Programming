# 02 - Vehicle Registration - Easy

## Question Details
- Concept: Variables and naming conventions
- Supporting concepts: Strings, numeric values, validation, formatted output
- Difficulty: Easy
- Domain: Vehicle registration
- Learning Objective: Store related vehicle information in clearly named variables and produce a readable registration summary.

## Scenario
A dealership records basic information before a vehicle is delivered. The registration record uses a vehicle identification number (VIN), model year, mileage in km, and fuel type.

## Function Details
- Function signature: `create_registration(vin: str, model_year: int, mileage_km: int, fuel_type: str) -> str`
- Behavior / return shape: Create a validated registration summary for one vehicle.
- Exact accepted inputs: `vin`: exactly 17 uppercase letters or digits; `model_year`: integer from 1886 through 2100; `mileage_km`: integer from 0 through 2,000,000; `fuel_type`: one of `PETROL`, `DIESEL`, `HYBRID`, or `ELECTRIC`.
- Output and validation / behavior: Return: `VIN=<vin>; Year=<year>; Mileage=<mileage> km; Fuel=<fuel>`.

## Tasks to Implement
1. Implement `create_registration` with the exact signature above and validate the inputs against these accepted rules: `vin`: exactly 17 uppercase letters or digits; `model_year`: integer from 1886 through 2100; `mileage_km`: integer from 0 through 2,000,000; `fuel_type`: one of `PETROL`, `DIESEL`, `HYBRID`, or `ELECTRIC`.
2. Create a validated registration summary for one vehicle.
3. Return exactly the specified result: Return: `VIN=<vin>; Year=<year>; Mileage=<mileage> km; Fuel=<fuel>`.

## Test Cases
| # | Call | Expected Output | Why this case matters |
| --- | --- | --- | --- |
| 1 | create_registration("1HGCM82633A004352", 2020, 0, "ELECTRIC") | VIN=1HGCM82633A004352; Year=2020; Mileage=0 km; Fuel=ELECTRIC | Typical valid input. |
| 2 | create_registration("WVWZZZ1JZXW000001", 1886, 1, "PETROL") | VIN=WVWZZZ1JZXW000001; Year=1886; Mileage=1 km; Fuel=PETROL | Valid boundary or threshold case. |
| 3 | create_registration("JH4KA8260MC000001", 2100, 2000000, "DIESEL") | VIN=JH4KA8260MC000001; Year=2100; Mileage=2000000 km; Fuel=DIESEL | Checks an alternate accepted value or input shape. |
| 4 | create_registration("5YJSA1E26HF000001", 2024, 12500, "HYBRID") | VIN=5YJSA1E26HF000001; Year=2024; Mileage=12500 km; Fuel=HYBRID | Checks a second valid boundary or aggregation case. |
| 5 | create_registration("ABCDEF12345678901", 2000, 0, "ELECTRIC") | VIN=ABCDEF12345678901; Year=2000; Mileage=0 km; Fuel=ELECTRIC | Checks another valid input without changing the contract. |

## Expected Deliverables
- Complete implementation of create_registration that satisfies the specification.
- A brief explanation of the approach and the logic used.
- Test evidence demonstrating the function works across the supplied valid-case scenarios.

## Additional Guidance
### Prerequisites
Assignment statements, strings, numbers, print(), and basic conditionals.

### Rules and Constraints
- Use descriptive snake_case variable names.
- Reject invalid values with ValueError.
- Preserve the uppercase fuel value.
- Do not use global variables.

### Hints
- Correctness: 3 points
- Variable use and naming: 1 point
- Input validation: 1 point
- Edge-case handling: 1 point
- Readability: 1 point
- Modularity: 1 point
- Efficiency: 0.5 point
- Documentation: 0.5 point
- Testability: 1 point
1. Store each parameter in a clearly named local variable if needed.
2. Validate the VIN length and allowed characters.
3. Use an f-string for the final line.

### Hint Rubric
- Validate that vin is exactly 17 characters and contains only uppercase letters and digits.
- Ensure model_year is between 1886 and 2100 inclusive.
- Ensure mileage_km is between 0 and 2_000_000 inclusive.
- Confirm fuel_type is one of PETROL, DIESEL, HYBRID, ELECTRIC.
- Construct the output string with an f‑string matching the required format.

### Common Mistakes
- Using unclear names such as x and y.
- Accepting invalid fuel labels.
- Allowing negative mileage.
- Changing the required output punctuation.

### Extension Challenge
Add an optional owner_id field with validation while preserving backward compatibility.
