# Against All Odds — Week 8 Logistic Regression and Elo

Generated: 2026-10-11T02:27:45+00:00

Week 8 built the project's first serious predictive models.

Separate logistic-regression models were trained for the NBA, NFL, and Premier
League. Logistic regression was interpreted using coefficients, odds ratios,
statistical significance, and predicted probabilities.

Elo ratings were rebuilt chronologically. For each game, the pre-game ratings
and Elo probability were stored before the current result was used to update
the ratings.

NFL ties and Premier League draws contribute 0.5 to the Elo update.

Logistic regression and Elo were compared on VALIDATION using accuracy,
precision, recall, F1, ROC-AUC, Brier score, and log loss.

TEST remained held out by default.
