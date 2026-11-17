---
layout: default
---

# 04-Strings-Trip Summary Exercise

**Difficulty:** Difficult  
**Primary Python Concept:** Strings, formatting, and structured text generation  
**Supporting Concepts:** Dictionaries, lists, validation, aggregation  
**Automotive Domain:** Trip‑computer summary  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Generate a stable multi‑line text report from structured trip data while handling validation and rounding.

---

## Problem Statement
**Goal:** Generate a stable multi‑line text report from structured trip data while handling validation and rounding.

**Specifically:** Implement a function that receives a list of segment dictionaries and returns a formatted trip‑summary report.

```python
from typing import List, Dict

def build_trip_summary(segments: List[Dict[str, float]]) -> str:
    """Return a five‑line report summarising the trip.

    The report must contain exactly the following lines (including the newline
    characters between them):

    1. `Distance: X.XX km`
    2. `Fuel: Y.YY L`
    3. `Economy: Z.ZZ L/100km`
    4. `Average segment speed: A.AA km/h`
    5. `Longest segment: N`

    *All numeric values are rounded to two decimal places.*

    Validation rules (raise `ValueError` on any violation):
    * Each segment is a ``dict`` with keys ``distance_km``, ``fuel_liters``,
      ``average_speed_kmh``.
    * All three values are ``float`` (or ``int``) and lie within the ranges
      described in the specification.
    * At least one segment must have a **positive** distance.
    * The input list must contain 1 – 1,000 items.
    * The function must **not** mutate the input data.
    """
    raise NotImplementedError
```

---

## Hints
1. Validate each segment before any aggregation.
2. Keep track of the longest distance and its **first** index (1‑based).
3. Economy = ``total_fuel / total_distance * 100`` (``0`` when total fuel is ``0``).
4. Average speed = arithmetic mean of the ``average_speed_kmh`` values.
5. Use f‑strings with ``:.2f`` for formatting; do **not** round intermediate
   totals.

---
