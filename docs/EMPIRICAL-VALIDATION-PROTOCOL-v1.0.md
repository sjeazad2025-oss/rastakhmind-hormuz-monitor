# Rastakhmind Simulation Engine v2.0 — Empirical Validation Protocol v1.0

## Purpose

This document converts the repository from a **methodologically separated simulation record** into a framework capable of **empirical model validation**.

Important distinction:

> A model cannot be made empirically proven merely by documenting its outputs. Empirical support must come from reproducible tests against observations that were not used to construct or calibrate the forecast.

The target status is therefore **EMPIRICALLY VALIDATED FOR A DEFINED TASK AND DATA DOMAIN**, not absolute proof of future reality.

## 1. Validation target

The primary validation target is the model's ability to forecast whether the monitored systemic-risk state crosses the configured threshold `s_crit = 0.18` in a future observation window.

Secondary targets:

- calibration of `ΔC` against independently measured congestion/pressure indicators;
- directional accuracy of the risk trajectory;
- stability under parameter perturbation;
- false-positive and false-negative rates;
- reproducibility from a frozen input dataset and model version.

## 2. Data separation

Validation must use three non-overlapping data roles:

1. **Training/calibration set** — may be used to estimate parameters.
2. **Validation set** — used for model selection and sensitivity checks.
3. **Locked holdout set** — never used during calibration or model selection; opened only for the final evaluation.

No future observation may be fed backward into the model before its forecast is evaluated.

## 3. Required evidence package

A validation claim requires all of the following artifacts:

- timestamped raw observations;
- source identifiers and geographic scope;
- frozen preprocessing rules;
- exact model version or commit SHA;
- exact parameter file;
- reproducible execution instructions;
- predicted values and prediction timestamps;
- observed outcomes for the same horizons;
- an automated scoring report;
- the complete locked holdout definition.

If any required artifact is missing, the result remains **NOT VALIDATED** rather than being upgraded by inference.

## 4. Pre-registered acceptance criteria

For the threshold-crossing task, the evaluation must report at minimum:

- accuracy;
- precision;
- recall/sensitivity;
- specificity;
- F1 score;
- false-positive rate;
- false-negative rate;
- Brier score or another proper probabilistic score when probabilistic forecasts are available;
- confusion matrix;
- calibration analysis where probabilities are produced.

Threshold performance must be compared with at least one transparent baseline model. A result is not considered evidence of predictive skill merely because the Rastakhmind model performs consistently with a naive persistence or trend baseline.

## 5. Statistical robustness

Where sample size permits, confidence intervals must be reported. Time-series dependence must be respected; random shuffling of temporally adjacent observations is not an acceptable substitute for chronological validation.

Sensitivity analysis must perturb `α`, `β`, relevant input weights, and threshold assumptions over a documented range. The report must identify whether the principal conclusion survives those perturbations.

## 6. Backtesting rule

For every historical evaluation date `T`:

1. freeze all information available at `T`;
2. generate the forecast for `T + h`;
3. record the forecast without modification;
4. wait for the corresponding observed outcome;
5. score the forecast against that outcome;
6. repeat chronologically across the evaluation window.

This creates a walk-forward test and prevents hindsight leakage.

## 7. Reproducibility gate

A model version may be labeled **EMPIRICALLY VALIDATED** only after an independent rerun reproduces the published scoring results from the frozen dataset and exact model version.

The minimum state machine is:

`DOCUMENTED → REPRODUCIBLE → BACKTESTED → HOLDOUT-TESTED → INDEPENDENTLY REPRODUCED → EMPIRICALLY VALIDATED`

The current repository state should not skip intermediate states.

## 8. Current status

As of 31 October 2026, the repository has a strong evidence-separation methodology, but the public record does not yet contain the complete frozen dataset, executable validation harness, locked holdout evaluation, and independent reproduction required for the final `EMPIRICALLY VALIDATED` label.

Therefore:

**CURRENT VALIDATION STATUS = NOT YET EMPIRICALLY VALIDATED**

This is a deliberate research-control state, not a failure of the model. It identifies exactly what evidence must be produced before a stronger scientific claim is justified.

## 9. Non-negotiable reporting rule

Never convert:

`model output → observed fact`

or:

`successful historical fit → proven future behavior`.

A successful validation result supports a bounded claim such as:

> "Under the stated data domain, forecast horizon, preprocessing, model version, and evaluation protocol, Rastakhmind Engine v2.0 demonstrated predictive performance exceeding the specified baseline on the locked holdout dataset."

That is the strongest scientifically defensible form of a validation claim unless substantially broader evidence is available.
