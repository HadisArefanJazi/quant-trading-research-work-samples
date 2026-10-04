# Validation Method: Matched-Control Event Study

This document describes the historical validation framework used for the proprietary Settlement Pivot market-structure edge.

Only aggregate, non-reconstruction-enabling information is presented.

---

## Research Question

The central research question is:

> When the proprietary scanner identifies a post-confirmed market-structure event, does subsequent market behavior differ from otherwise comparable market observations where the edge was not present?

The objective is not simply to calculate a signal success rate.

The objective is to test whether the scanner provides **incremental information relative to a matched market baseline**.

---

## Evaluation Sample

**Instrument:** XAUUSD

**Evaluation period:** January 2021 through August 2026

**Primary timeframes:** M30 and H1

The analysis compares historical scanner events with matched non-signal market observations.

---

## Validation Workflow

The validation follows the sequence:

**Detect -> Confirm -> Match -> Evaluate -> Compare**

1. Detect a proprietary market-structure edge event.
2. Apply a standardized post-confirmation rule.
3. Match the event with comparable non-signal observations.
4. Apply the same future-outcome test to both groups.
5. Compare their success rates.
6. Measure the difference as lift in percentage points.

---

## Edge Versus Entry

The Settlement Pivot edge is not treated as a standalone trading entry.

It identifies a higher-level market context in which a partial settlement, correction, or reversal may become more likely.

Practical execution requires separate evidence of momentum change on a lower fractal or timeframe.

For historical validation, I used a deliberately simple standardized close-based confirmation proxy. This creates a consistent event definition without claiming that the confirmation rule is the only or optimal execution method.

---

## Standardized Post-Confirmation

Final confirmation and adverse reference breaks are evaluated using candle closes.

The validation framework permits one adverse reference replacement. A second adverse break invalidates the setup.

This rule is used to standardize the historical experiment and is separate from the proprietary logic that generates the underlying market-structure edge.

---

## Primary Outcome Definition

For both signal observations and matched controls, the primary outcome asks whether price reaches:

- **+1.0 ATR** in the evaluated direction,
- before reaching **-0.5 ATR** adverse movement,
- within a maximum horizon of **30 bars**.

ATR normalization is used so that target and invalidation distances adjust to the volatility environment rather than relying on a fixed price distance.

Exactly the same future-outcome definition is applied to both signal and control observations.

---

## Same-Bar Ambiguity

In some observations, both the +1.0 ATR target and the -0.5 ATR invalidation level are reached within the same bar.

With bar-level data, the order in which those two levels were reached cannot be determined reliably.

These observations are classified as:

`AMBIGUOUS_SAME_BAR`

They are excluded from the primary success-rate calculation.

Therefore:

- **Total N** represents all observations in the sample.
- **Evaluable N** represents observations for which target-versus-invalidation ordering can be determined from the available data.

The reported primary success rates are calculated using Evaluable N.

---

## Matched-Control Design

Each signal event is paired with five non-signal control observations selected from comparable market conditions.

Matching considers:

- the same timeframe,
- the same evaluated bullish or bearish direction,
- similar market timing,
- and a similar volatility regime.

The future outcome is never used to select controls.

The objective is not to reproduce an identical historical market state. Instead, matching provides a more relevant comparison than using unconditional random market observations.

Each control remains associated with its originating signal through a parent signal identifier.

---

## Why Use a Matched Baseline?

A raw signal success rate is not sufficient evidence of an edge.

The market may reach the same target at a meaningful rate even when no scanner signal exists.

The relevant question is therefore:

> Does the event identified by the scanner have a higher probability of the defined favorable outcome than comparable market observations without that event?

The difference is reported as:

**Lift (percentage points) = Signal Success Rate - Matched Baseline Success Rate**

A positive lift means that scanner-identified observations historically produced the defined favorable outcome more often than their matched controls.

---

## Historical Results

| Segment | Signal Total N | Signal Evaluable N | Control Total N | Control Evaluable N | Signal Success | Matched Baseline | Lift |
|---|---:|---:|---:|---:|---:|---:|---:|
| Overall M30+H1 | 234 | 220 | 1,170 | 1,107 | 40.9% | 35.7% | +5.2 pp |
| M30 overall | 166 | 154 | 830 | 788 | 41.6% | 36.9% | +4.6 pp |
| M30 Bullish | 69 | 64 | 345 | 332 | 45.3% | 37.3% | +8.0 pp |
| H1 overall | 68 | 66 | 340 | 319 | 39.4% | 32.6% | +6.8 pp |
| H1 Bearish | 38 | 36 | 190 | 178 | 41.7% | 29.2% | +12.5 pp |

For the overall M30 + H1 sample, the scanner generated **234 signal observations**.

Fourteen signal observations were classified as same-bar ambiguous, leaving **220 evaluable signal observations**.

The corresponding matched-control sample contained **1,170 observations**, of which **1,107 were evaluable**.

The resulting primary comparison was:

**40.9% signal success versus 35.7% matched baseline, corresponding to +5.2 percentage points of historical lift.**

---

## Conservative Ambiguity Check

As a sensitivity check, all same-bar ambiguous observations can instead be treated as failures.

Under this more conservative assumption:

- Signal success rate: **90 / 234 = 38.5%**
- Matched baseline success rate: **395 / 1,170 = 33.8%**
- Lift: approximately **+4.7 percentage points**

The overall lift therefore remains positive under this stricter treatment of ambiguous observations.

This is a sensitivity check and not the primary reported methodology.

---

## Year-by-Year Consistency

The M30 Bullish segment showed positive historical lift in each annual signal cohort from 2021 through August 2026.

For annual analysis, matched controls remain associated with the year of their parent signal so that the original signal-control cohort structure is preserved.

This result is interpreted as **historical consistency**, not as evidence that future yearly performance will necessarily remain positive.

---

## Interpretation

The purpose of this experiment is to test whether the scanner identifies market conditions containing additional information relative to a matched non-signal baseline.

The results are best described as:

**historical evidence of conditional lift.**

They are not equivalent to:

- a complete trading-strategy backtest,
- proof of persistent alpha,
- evidence of guaranteed profitability,
- or a fully out-of-sample demonstration of future performance.

The edge-detection layer and the trade-execution layer should therefore be evaluated separately.

---

## Important Limitations

The current analysis has several important limitations:

- some subgroups have relatively small sample sizes,
- results may be sensitive to the control-matching specification,
- bar-level data create ordering ambiguity in some observations,
- the current public evidence focuses on XAUUSD,
- edge detection is not equivalent to a complete entry/exit strategy,
- confidence intervals and formal statistical-significance estimates are not currently presented,
- and further fully out-of-sample and cross-instrument validation would strengthen the evidence.

Future research can include alternative matching specifications, statistical uncertainty estimates, additional instruments, and explicitly held-out samples.

---

## Proprietary Information

Scanner rules, thresholds, parameterization, and reconstruction-enabling implementation details are intentionally withheld.

The purpose of this public work sample is to demonstrate:

**Research Question -> Formalization -> Implementation -> Validation**

without disclosing the proprietary mechanism that generates the underlying edge.

---

Historical research evidence only. Not a guarantee of future performance.
