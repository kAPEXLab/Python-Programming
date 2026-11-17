# 12_ListsAndSlicing_BatterySamples

**Difficulty:** Medium  
**Primary Python Concept:** List slicing with a step  
**Supporting Concepts:** Validation, aggregation, rounding, functions  
**Automotive Domain:** Offline battery voltage sampling

## Learning Objective
Use slices with start, stop, and step values to separate alternating battery samples.

## Prerequisites
Lists, slicing, arithmetic, dictionaries, functions, and exceptions.

## Scenario Introduction
A battery test bench is recording voltage readings from a charging cycle while two sensor groups alternate in sequence. The first, third, fifth, and later readings belong to Channel A, while the second, fourth, and later readings belong to Channel B. Your task is to summarize the average voltage for each channel and confirm the total number of samples captured before the report is logged.

## Problem Statement
**Goal:** Use slices with start, stop, and step values to separate alternating battery samples.

**Specifically:** Summarize the average voltage of both alternating channels and the complete sample count.

## Task to Implement
Implement `summarize_battery_samples(samples: list[float]) -> dict[str, object]`.

## Input Specification
Provide 2 through 200 finite voltage readings from 10.0 through 16.0 volts. Values are measured to at most three decimals.

## Output Specification
Use `samples[::2]` for channel A and `samples[1::2]` for channel B. Return `channel_a_average`, `channel_b_average`, and `sample_count`, with averages rounded to two decimals.

## Rules and Constraints
- Preserve input order and do not mutate input.
- Channel B may contain one fewer sample.
- Raise `ValueError` for invalid values or fewer than two samples.
- Use slicing to form both channels.

## Hints
1. Validate with `math.isfinite()` before averaging.
2. Build each channel with a slice step of two.
3. Apply `round(value, 2)` only to the final averages.

## Common Mistakes
- Taking contiguous halves instead of alternating samples.
- Rounding each input before averaging.
- Dividing by the total sample count.

## Extension Challenge
Return the channel with the larger average, or `"equal"` when the rounded averages match.
