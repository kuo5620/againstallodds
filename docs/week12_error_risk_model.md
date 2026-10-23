# Against All Odds — Week 12 Error-Risk Model

Generated: 2026-10-23T10:35:15+00:00

## Week 12 objective

Week 12 created a second model whose job is not to predict the winner of a
game. Instead, it estimates how likely the original winner prediction is to
be wrong.

## Target variables

For each historical prediction:

- PRIMARY_MODEL_CORRECT = 1 when the original winner prediction was correct.
- PRIMARY_MODEL_CORRECT = 0 when the original winner prediction was wrong.
- PRIMARY_MODEL_ERROR = 1 - PRIMARY_MODEL_CORRECT.

The Week 12 model predicts PRIMARY_MODEL_ERROR.

## Risk-model inputs

The project uses information motivated by the capstone draft:

- Original win probability
- Fragility Score
- Elo difference
- Team-strength difference
- Recent-form difference
- Model disagreement
- Rest difference
- Home advantage

A PRIMARY_PREDICTS_HOME indicator is also retained as a useful home-context
variable. Zero-variance variables are automatically removed before fitting.

## Chronological workflow

- Primary winner models are fit on TRAIN.
- Historical error-risk examples are created from VALIDATION.
- The error-risk model is trained on VALIDATION.
- Final error-risk performance is evaluated on TEST.

The held-out TEST outcomes are never used to train the winner model or the
error-risk model.

## Error-risk model

Separate balanced Logistic Regression error-risk models are trained for the
NBA, NFL, and Premier League. Balanced class weights are used because incorrect
winner predictions may be less common than correct predictions.

## Week 12 results

- NBA: ROC-AUC 0.629, error recall 0.661, F1 0.485, Brier score 0.240.
- NFL: ROC-AUC 0.534, error recall 0.511, F1 0.454, Brier score 0.252.
- Premier League: ROC-AUC 0.627, error recall 0.633, F1 0.524, Brier score 0.238.

## Interpretation

A larger ERROR_RISK_PROBABILITY means the system believes the original winner
prediction has a greater chance of being wrong. This probability does not
replace the winner prediction. It is an additional reliability measure that
will be combined with probability calibration, the Fragility Score, and model
disagreement during Week 13.

## Next step

Week 13 combines winner prediction, probability calibration, Fragility Score,
error-risk probability, and model disagreement to create the Against All Odds
Unpredictability Index and Predict / Caution / Abstain system.
