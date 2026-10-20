# Against All Odds — Week 11 Fragility Score

Generated: 2026-10-20T02:45:53+00:00

## Week 11 objective

Week 11 created the original Against All Odds Fragility Score.

The purpose of the score is to measure how easily a model's predicted winner
can change when important pre-game information is changed slightly.

## Variables tested

- ELO_DIFF
- FORM_DIFF
- OFFENSE_DIFF
- DEFENSE_DIFF
- REST_DIFF

Player availability was not included because the current primary prediction
models do not contain a reliable player-availability feature.

## Method

For each TEST game:

1. Generate the original calibrated winner probability.
2. Record the original predicted winner.
3. Change one important pre-game variable at a time.
4. Move the variable upward and downward in 0.25-standard-deviation steps.
5. Recalculate the calibrated probability after every change.
6. Stop when the predicted winner changes.
7. Record the smallest standardized change that caused a winner flip.

The search stops at 4.0 standard deviations.

## Fragility Score

Fragility Score = 100 × (1 - capped minimum flip distance / 4.0)

A high score means that only a small change was needed to flip the prediction.
A low score means the prediction was harder to change.

## Categories

- Stable: 0–<25
- Moderate: 25–<50
- Fragile: 50–<75
- Extremely Fragile: 75–100

## Results

- NBA: mean Fragility Score 63.75; 542 extremely fragile, 380 fragile, 209 moderate, 78 stable.
- NFL: mean Fragility Score 61.76; 102 extremely fragile, 85 fragile, 49 moderate, 19 stable.
- Premier League: mean Fragility Score 56.57; 136 extremely fragile, 116 fragile, 59 moderate, 59 stable.

## Data protection

The primary model is fit on TRAIN. Probability calibration is fit on
VALIDATION. Fragility is measured on TEST. Actual TEST outcomes are not used
to search for the counterfactual change that flips the predicted winner.

## Next step

Week 12 will use the winner prediction, calibrated probability, Fragility
Score, team-strength information, and other reliability information to build
the prediction Error-Risk Model.
