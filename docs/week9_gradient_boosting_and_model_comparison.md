# Against All Odds — Week 9 Gradient Boosting and Model Comparison

Generated: 2026-10-11T23:57:08+00:00

## Week 9 objective

Week 9 built one advanced nonlinear winner-prediction model using Gradient
Boosting.

A separate Gradient Boosting model was trained for:
- NBA
- NFL
- Premier League

## Feature set

The same leakage-safe pre-game difference features created during Week 6 were
used:

- ELO_DIFF
- WIN_PCT_DIFF
- FORM_DIFF
- POINT_GOAL_DIFF
- OFFENSE_DIFF
- DEFENSE_DIFF
- REST_DIFF
- SCHEDULE_STRENGTH_DIFF

## Gradient Boosting configuration

{
  "n_estimators": 150,
  "learning_rate": 0.05,
  "max_depth": 3,
  "min_samples_leaf": 10,
  "subsample": 0.9,
  "random_state": 42
}

The capstone draft specifically says not to spend excessive time
hyperparameter tuning, so one reasonable configuration was used consistently.

## Model comparison

Gradient Boosting was compared against:
- Always-home baseline
- Better-record baseline
- Higher-Elo baseline
- Elo
- Logistic Regression

Required Week 9 metrics:
- Accuracy
- ROC-AUC
- F1
- Brier score
- Log loss

## Best primary validation model by sport

- NBA: Logistic Regression (accuracy=0.663, ROC-AUC=0.720, F1=0.709, Brier=0.211, log loss=0.609)
- NFL: Elo (accuracy=0.676, ROC-AUC=0.723, F1=0.681, Brier=0.216, log loss=0.623)
- Premier League: Logistic Regression (accuracy=0.651, ROC-AUC=0.704, F1=0.583, Brier=0.215, log loss=0.616)

## Data split

Gradient Boosting was fit on TRAIN and evaluated on VALIDATION.
TEST remained held out by default.

## Next step

Week 10 will focus on probability calibration and whether predicted
probabilities can be trusted.
