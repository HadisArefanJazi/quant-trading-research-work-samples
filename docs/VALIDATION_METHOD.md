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

## Same-bar ambiguity handling

In some observations, both the +1.0 ATR target and the -0.5 ATR invalidation level were reached within the same bar. Because bar-level data cannot determine which level was reached first, these observations are classified as `AMBIGUOUS_SAME_BAR`.

These ambiguous observations are excluded from the primary success-rate calculation. Therefore, reported success rates use only observations for which the target-versus-invalidation ordering can be determined from the available data.

## Matching variables

For each signal event, five non-signal control observations were selected from comparable market conditions.

Matching considered:

- timeframe,
- bullish or bearish evaluation direction,
- market timing / session context,
- and volatility regime.

The future outcome was never used in selecting control observations.

The purpose of matching was not to recreate an identical market state, but to create a more relevant baseline than unconditional random observations.

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


## Important limitations

These results should be interpreted as historical evidence of conditional lift, not as proof of persistent future alpha.

Important limitations include:

- relatively small sample sizes in some subgroups,
- potential sensitivity to the matching definition,
- the distinction between edge detection and actual trade execution,
- and the need for further out-of-sample and cross-instrument testing.

Scanner implementation details, thresholds, signal rules, and event-level raw data are intentionally withheld to protect proprietary work.
