# Against All Odds — Week 10 Probability Calibration

Generated: 2026-10-12T01:11:22+00:00

## Objective

Week 10 determines whether the selected primary winner-model probabilities can
actually be trusted. A well-calibrated model should have observed outcomes that
approximately match predicted probabilities.

## Calibration design

- Primary model selection: Week 9
- Base model fit: TRAIN
- Calibration method: Platt scaling
- Calibration fit: VALIDATION
- Calibration evaluation: TEST

TEST was not used to fit the base model or the calibrator.

## Required Week 10 outputs

- Calibration curves
- Brier score
- Log loss
- Reliability tables
- Calibrated winner probabilities

## Raw versus calibrated TEST results

- NBA (Logistic Regression): Brier 0.2072 -> 0.2073; log loss 0.6025 -> 0.6028.
- NFL (Elo): Brier 0.2363 -> 0.2400; log loss 0.6673 -> 0.6798.
- Premier League (Logistic Regression): Brier 0.2266 -> 0.2238; log loss 0.6444 -> 0.6378.

Lower Brier score and lower log loss indicate better probability quality.

## Next step

Week 11 will use the calibrated winner probabilities in the Against All Odds
Fragility Score analysis.
