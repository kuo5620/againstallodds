# Against All Odds — Week 6 Feature Engineering

Generated: 2026-10-05T02:12:18+00:00

## Week 6 deliverable

Three leakage-safe model-ready datasets were created:

- data/model_ready/nba/nba_model_ready_2021_22_to_2025_26.csv
- data/model_ready/nfl/nfl_model_ready_2021_to_2025.csv
- data/model_ready/soccer/premier_league_model_ready_2021_22_to_2025_26.csv

## Core feature groups

### Team strength
- Pre-game win percentage
- Pre-game Elo
- Historical point/goal differential

### Recent form
- Last 3
- Last 5
- Last 10 where appropriate

### Offense
- Historical points/goals scored
- Recent scoring
- NBA efficiency metrics where available
- Premier League shots/shots-on-target where available

### Defense
- Historical points/goals allowed
- Recent defensive performance
- NBA defensive rating where available

### Context
- Home-team perspective
- Rest
- Current opponent Elo
- Recent schedule strength

### Matchup differences
- ELO_DIFF
- WIN_PCT_DIFF
- FORM_DIFF
- POINT_GOAL_DIFF
- OFFENSE_DIFF
- DEFENSE_DIFF
- REST_DIFF
- SCHEDULE_STRENGTH_DIFF

## Leakage prevention

Every historical expanding or rolling feature applies shift(1) before the
calculation. The current game's final score, result, and box/match statistics
cannot enter that game's pre-game predictor values.

The final model-ready CSV files intentionally keep HOME_WIN as the target while
excluding current-game final scores and current-game box/match statistics from
the predictor columns.

## Sport-specific handling

### NBA
HOME_WIN is binary. Historical NBA efficiency statistics are used only when
those fields are present in the clean Week 3 data.

### NFL
A tie contributes 0.5 to historical team-strength and Elo updates. Tied games
are excluded from the final binary HOME_WIN modeling dataset.

### Premier League
HOME_WIN equals 1 only for a home win. Draws and away wins equal 0 for the
binary target. Draws contribute 0.5 to Elo updates.

## Next step

Week 7 will use these model-ready datasets for exploratory data analysis and
baseline predictions.
