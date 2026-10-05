## Week 6 — Feature Engineering

Created leakage-safe pre-game features for the NBA, NFL, and Premier League.
Features include pre-game win percentage, Elo, point/goal differential, recent
form, offense, defense, rest, opponent strength, schedule strength, and matchup
difference variables. All rolling historical calculations use `shift(1)` so
the current game cannot use information from itself. Three model-ready datasets
were produced for Week 7 exploratory analysis and baseline modeling.
