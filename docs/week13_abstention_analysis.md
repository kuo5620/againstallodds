# Against All Odds — Week 13B Abstention Analysis

Generated: 2026-10-25T14:27:53+00:00

The abstention experiment tests whether prediction accuracy improves when the system refuses to predict the games with the highest Unpredictability Index.

Games are ranked from lowest to highest uncertainty. Accuracy is then measured while retaining 100%, 90%, 80%, 70%, and 60% of games.

- NBA: accuracy changed from 69.0% at 100% coverage to 75.2% at 60% coverage.
- NFL: accuracy changed from 63.9% at 100% coverage to 68.0% at 60% coverage.
- Premier League: accuracy changed from 62.4% at 100% coverage to 68.5% at 60% coverage.

Coverage is the share of games still receiving a prediction. Risk is the prediction error rate among retained games. If the reliability system works well, removing the highest-risk games should generally reduce error and improve accuracy.
