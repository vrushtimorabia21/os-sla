# SJF and SRTF Scheduling Simulator

A browser-based CPU scheduling simulator that compares **Non-Preemptive SJF** (Shortest Job Next) and **Preemptive SJF** (Shortest Remaining Time First, SRTF). It is a web version of the original C program for the Operating System self-learning activity (Review 2).

**Members:** Vrushti Morabia (33/125BTCM1117), Jinsiha Rathod (48/125BTCM1035)

## Features

- Add up to 20 processes with arrival and burst times
- Input validation: whole numbers only, arrival 0-1000, burst 1-1000
- Run Non-Preemptive SJF, Preemptive SRTF, or both side by side
- Colour-coded Gantt chart with time ticks and hatched idle periods
- Per-process table: Arrival (AT), Burst (BT), Completion (CT), Turnaround (TAT), Waiting (WT) and Response (RT) times
- Summary metrics: average WT, TAT and RT, context switches, throughput and CPU utilization
- Comparison table that shows which algorithm has the lower average waiting time and fewer context switches
- "Load example" button, responsive layout, and automatic light/dark theme

## Getting started

1. Download `sjf_scheduling.html`.
2. Open it in any modern browser (Chrome, Edge, Firefox, Safari).
3. No build step, server or dependencies are needed.

## How to use

1. Enter the arrival and burst time for each process. Use **Add process** or **Remove** to change the number of rows, or **Load example** for sample data.
2. Choose an algorithm: Non-Preemptive SJF, Preemptive SJF (SRTF), or Both (compare).
3. Click **Run simulation** to see the Gantt chart, tables and metrics.

## Example input

| Process | Arrival | Burst |
|---------|---------|-------|
| P1      | 0       | 8     |
| P2      | 1       | 4     |
| P3      | 2       | 9     |
| P4      | 3       | 5     |

## How it works

| Algorithm | Behaviour |
|-----------|-----------|
| Non-Preemptive SJF | When the CPU is free, it picks the arrived process with the smallest burst time and runs it to completion. |
| Preemptive SRTF | Every 1 ms it picks the arrived process with the smallest remaining time, so a shorter new arrival can preempt the running process. |

- Ties are broken by earlier arrival, then by lower process ID.
- If no process has arrived, the CPU sits idle until the next arrival.
- Formulas: `TAT = CT - AT`, `WT = TAT - BT`, `RT = first start - AT`.
- A context switch is counted when the CPU passes directly from one process to a different one. Idle gaps are not counted.
- Throughput = processes / total time. CPU utilization = busy time / total time.

## Assumptions

- Single CPU core
- Integer time units (ms)
- Burst times are known in advance
- Context-switch overhead is zero

## Tech stack

HTML, CSS and vanilla JavaScript in one file, with no frameworks or external libraries.

## Project structure

```
sjf_scheduling.html   # markup, styles and scheduling logic
README.md
```
