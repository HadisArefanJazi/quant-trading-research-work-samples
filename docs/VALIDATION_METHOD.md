# Validation Method: Matched-Control Event Study

This repository presents only aggregate, non-sensitive validation evidence.

## What is the method called?

The evaluation is a **matched-control event study** (also described in the work sample as
**matched-baseline historical validation**).

The central question is:

> When the proprietary edge produces a post-confirmed event, does the subsequent market
> behavior differ from otherwise similar market observations where no signal was present?

## Simple workflow

1. **Detect the edge event** using the proprietary Settlement Pivot scanner.
2. **Require a standardized post-confirmation** before the event is evaluated.
3. **Define one objective outcome** for both signal and control observations.
4. **Match each signal with five non-signal controls** under similar conditions.
5. **Run the same event test** on signals and controls.
6. **Compare success rates** and report the absolute lift in percentage points.

## Outcome used in the reported experiment

The primary event test asked whether price reached:

- **+1.0 ATR** in the predicted direction
- before reaching **-0.5 ATR** adverse movement
- within a **30-bar horizon**.

Only resolved events are used in the reported success-rate comparison.

## Matching variables

Controls were selected to be similar to the corresponding signal observation in:

- timeframe,
- market timing,
- and volatility regime.

The future outcome was not used to select controls.

## Why use a matched baseline?

A raw signal success rate is not sufficient by itself because the market may reach the
same target at a meaningful rate even without the signal.

The matched-control design asks whether the signal identifies observations with better
subsequent behavior than comparable non-signal observations.

## Reported evidence

| Segment | N | Signal | Matched baseline | Lift |
|---|---:|---:|---:|---:|
| Overall M30+H1 | 234 | 40.9% | 35.7% | +5.2 pp |
| M30 overall | 166 | 41.6% | 36.9% | +4.6 pp |
| M30 Bullish | 69 | 45.3% | 37.3% | +8.0 pp |
| H1 overall | 68 | 39.4% | 32.6% | +6.8 pp |
| H1 Bearish | 38 | 41.7% | 29.2% | +12.5 pp |

M30 Bullish showed positive lift in each calendar year from 2021 through August 2026.

## Important limitation

These are historical research results, not proof of persistent future alpha. Scanner
implementation details, thresholds, signal rules, and event-level raw data are withheld
to protect proprietary work.
