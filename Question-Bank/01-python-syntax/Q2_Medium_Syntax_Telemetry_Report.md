# 01_PythonSyntax_TelemetryReport

**Difficulty:** Medium  
**Primary Python Concept:** Python syntax and program structure  
**Supporting Concepts:** Functions, lists, loops, conditionals, formatted output  
**Automotive Domain:** Vehicle telemetry  
**Estimated Completion Time:** 35 minutes

## Problem Statement
**Your goal:** Structure a multi‑step Python program that processes telemetry records and returns a deterministic report. Each simulated record contains a timestamp (seconds) and vehicle speed (km/h). The function must count how many readings are at or above a configurable speed limit and calculate the average speed.

## Hint Rubric
- Validate each tuple: correct length, timestamp is non‑negative integer, speed is a number within 0‑300.
- Validate `speed_limit` is within 0‑300.
- Do **not** modify the input list.
- Use a running sum for speeds and a separate counter for over‑limit readings.
- When `readings` is empty, average speed should be `0.00`.
- Format the final string exactly as:
  ```text
  Readings: N\nAverage speed: X.XX km/h\nOver limit: M
  ```
- Round the displayed average using `f"{avg:.2f}"`.
