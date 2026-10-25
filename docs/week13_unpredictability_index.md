# Against All Odds — Week 13A Unpredictability Index

Generated: 2026-10-25T14:26:35+00:00

Week 13 combines winner prediction, calibrated probability, Fragility Score, error-risk probability, and model disagreement into the Against All Odds Unpredictability Index.

The capstone draft does not give an exact formula, so this implementation uses four equally weighted 0–100 uncertainty components: calibrated probability uncertainty, Fragility Score, error-risk probability, and model disagreement. Higher scores mean more uncertainty.

Categories:
- Predict: low uncertainty, below 33.33
- Caution: moderate uncertainty, 33.33 to below 66.67
- Abstain: very high uncertainty, at least 66.67

TEST summary:
- NBA: mean index 47.25; prediction accuracy 69.0%.
- NFL: mean index 48.20; prediction accuracy 63.9%.
- Premier League: mean index 48.28; prediction accuracy 62.4%.

Notebook 16 uses this index for the required abstention experiment.
