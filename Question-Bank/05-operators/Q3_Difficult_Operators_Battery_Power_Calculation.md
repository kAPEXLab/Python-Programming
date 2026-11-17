---
layout: default
---

# 05_Operators_BatteryPowerCalculation

**Difficulty:** Difficult  
**Primary Python Concept:** Operator precedence and expressions  
**Supporting Concepts:** Unit conversion, aggregation, validation, rounding  
**Automotive Domain:** Electric-vehicle battery power analysis  
**Estimated Completion Time:** 55 minutes

## Learning Objective
Construct unambiguous expressions and calculate electrical power and energy from sampled voltage and current.

## Prerequisites
Lists, loops, arithmetic, boolean validation, and functions.

## Scenario Introduction
A simulated battery log contains voltage in volts, current in amperes, and sample duration in seconds. Instantaneous power is `voltage * current`; energy is power times time, converted from joules to watt-hours by dividing by 3,600.

## Problem Statement
**Goal:** Construct unambiguous expressions and calculate electrical power and energy from sampled voltage and current.

**Specifically:** Calculate total energy and peak power for a sequence of samples.

## Task to Implement
Implement `analyze_power_samples(samples: list[tuple[float, float, float]]) -> dict[str, float]`, returning `total_energy_wh` and `peak_power_w`.

## Input Specification
- One to 10,000 samples.
- Voltage: 0 through 1,000 V.
- Current: -500 through 500 A; negative means charging.
- Duration: 0.01 through 3,600 seconds.
- Reject malformed samples or invalid values with `ValueError`.

## Output Specification
For each sample, power is voltage times current. Total energy is the sum of `power * duration / 3600`. Return both fields rounded to two decimals.

## Rules and Constraints
- Parenthesize expressions where conversion order matters.
- Peak power is the largest absolute power, reported as a nonnegative value.
- Do not round intermediate products.
- Preserve no mutable global state.

## Hints
1. Calculate one sample's power before calculating its energy.
2. Divide joules by 3,600 only after multiplying power by seconds.
3. Use absolute power only for the peak comparison.

## Common Mistakes
- Dividing voltage or current by 3,600.
- Losing the negative sign for charging energy.
- Using signed power to calculate peak magnitude.

## Extension Challenge
Return separate positive discharge energy and negative charging energy totals.
