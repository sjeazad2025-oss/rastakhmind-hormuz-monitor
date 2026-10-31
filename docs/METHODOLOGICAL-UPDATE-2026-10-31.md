# Methodological Update — 31 October 2026

## Status

**Methodological state:** STRUCTURALLY SOUND  
**Scope:** Evidence-based maritime risk monitoring and simulation  
**Model reference:** Rastakhmind Simulation Engine v2.0

## Core methodological distinction

The monitor maintains an explicit separation between:

1. **OBSERVED / EXTERNAL** — independently sourced maritime observations and incident reports.
2. **EVIDENCE / SOURCE VALIDATION** — classification of those observations by evidentiary status.
3. **MODEL INPUTS** — calibrated values and parameters passed into the simulation.
4. **MODEL OUTPUT** — calculated states, forecasts, thresholds, and strategic-state values.
5. **INFERENCE / INTERPRETATION** — human analytical conclusions derived from the preceding layers.

The governing chain is:

`EXTERNAL DATA → EVIDENCE LAYER → MODEL INPUTS → SIMULATION → MODEL OUTPUT → SCENARIO FORECAST → EXTERNAL/HUMAN VALIDATION`

## Evidence discipline

The following rules are normative for this repository:

- **OBSERVATION ≠ MODEL**
- **MODEL ≠ REALITY**
- **FORECAST ≠ CONFIRMATION**
- A model crossing `s_crit` is a **model-state forecast**, not an independently confirmed real-world crisis.
- Reported observations retain their original uncertainty unless independently validated.
- Attribution claims must remain separate from the observation that prompted them.

## Current model values

The 31 October 2026 monitoring snapshot preserves the following model values:

| Metric | Value | Classification |
|---|---:|---|
| `ΔC` | 3.04 | Model output/calibration |
| `α` | 0.35 | Model parameter |
| `β` | 0.15 | Model parameter |
| `s_crit` | 0.18 | Model threshold |
| `s_1` | 0.1520 | Model output |
| `s_2` | 0.2429 | Model forecast |
| `s_4` | 0.3956 | Model forecast |

The numerical continuity of these values demonstrates continuity of the recorded simulation state. It **does not, by itself, establish empirical validity of the underlying model formulation, parameter calibration, or future-world assumptions**.

## Reproducibility and audit trail

The methodological update is preserved in Git history alongside the monitoring report so that future readers can distinguish:

- what was observed externally,
- what was classified as evidence,
- what the simulation calculated,
- what the model forecast,
- and what remains an interpretation requiring external validation.

This structure is intended to prevent retroactive blending of assumptions with facts and to preserve a reproducible research record.

## Research-status statement

The repository should be understood as an **evidence-governed monitoring and simulation record**, not as an authoritative real-time declaration of maritime conditions.

All externally sourced claims remain subject to source quality, coverage, timestamp, geographic scope, and independent corroboration.
