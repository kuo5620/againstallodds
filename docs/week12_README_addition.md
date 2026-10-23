## Week 12 — Error-Risk Model

Created a second model that estimates how likely the original winner prediction
is to be wrong. Historical predictions were labeled as correct or incorrect,
and the error-risk model used factors such as original win probability,
Fragility Score, Elo difference, team-strength difference, recent form, model
disagreement, rest, and home context. Separate models were trained for the NBA,
NFL, and Premier League using validation data and evaluated on the held-out test
data. The resulting error-risk probabilities will be used in the Week 13
Against All Odds Unpredictability Index.
