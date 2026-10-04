# Week 3 NBA Data Source and Cleaning Plan

Generated: {datetime.now(timezone.utc).isoformat(timespec="seconds")}

## Seasons
- 2021-22
- 2022-23
- 2023-24
- 2024-25
- 2025-26

## Source
Public NBA team game-log parquet files from:
https://github.com/llimllib/nba_data

The source repository documents the files as NBA team-level game logs sourced
from stats.nba.com.

## Season file mapping
- 2021-22 -> gamelog_2022.parquet
- 2022-23 -> gamelog_2023.parquet
- 2023-24 -> gamelog_2024.parquet
- 2024-25 -> gamelog_2025.parquet
- 2025-26 -> gamelog_2026.parquet

## Cleaning rules
1. Keep regular-season game IDs beginning with 002.
2. Keep the 30 canonical NBA franchises.
3. Standardize names from team abbreviations.
4. Convert game_date with pandas datetime parsing.
5. Drop duplicate team-game records by game_id + team_id.
6. Remove rows only when critical identifiers/outcomes are missing.
7. Require two team rows per game: one home and one away.
8. Build one game-level record per game.
9. Create HOME_WIN primarily from the official home/away W/L pair.
10. Repair tied source scores from plus/minus when the reconstruction agrees with W/L.
11. If a malformed tied score cannot be repaired, retain the official outcome and mark score-based derived fields missing.
12. Sort all records chronologically.

## Leakage rule
Current-game box-score and advanced statistics are post-game data.
They are retained as historical information only. Week 6 rolling predictors
must use shift(1) before rolling calculations.
