# Against All Odds — Week 2 Data-Source Plan

## Required sports

- NBA
- NFL
- Premier League

## Selected historical seasons

| sport          | included_seasons             | display_seasons         | training_period         | validation_period   | test_period   | reason                                            |
|:---------------|:-----------------------------|:------------------------|:------------------------|:--------------------|:--------------|:--------------------------------------------------|
| NBA            | 2021, 2022, 2023, 2024, 2025 | 2021-22 through 2025-26 | 2021-22 through 2023-24 | 2024-25             | 2025-26       | Five recent completed seasons; chronological h... |
| NFL            | 2021, 2022, 2023, 2024, 2025 | 2021 through 2025       | 2021 through 2023       | 2024                | 2025          | Five recent completed seasons; chronological h... |
| Premier League | 2122, 2223, 2324, 2425, 2526 | 2021-22 through 2025-26 | 2021-22 through 2023-24 | 2024-25             | 2025-26       | Five recent completed seasons with a consisten... |

## Source limitations

| sport          | source                 | limitation                                        | project_response                                  |
|:---------------|:-----------------------|:--------------------------------------------------|:--------------------------------------------------|
| NBA            | BALLDONTLIE NBA API    | API key required; some advanced/team-stat endp... | Use teams/games as the required core source. D... |
| NFL            | BALLDONTLIE NFL API    | API key required; detailed team/player/availab... | Use teams/games as the required core source. U... |
| Premier League | Football-Data.co.uk    | CSV schemas may vary by season and expected-go... | Use only columns consistently present across s... |
| ALL            | All historical sources | Final scores and match/game statistics are pos... | They may be used only to build historical roll... |

## Source-test audit

| sport          | test_name                                   | source                                            | status   |   http_status |   rows_returned |   columns_returned | notes                                             | tested_at_utc             |
|:---------------|:--------------------------------------------|:--------------------------------------------------|:---------|--------------:|----------------:|-------------------:|:--------------------------------------------------|:--------------------------|
| NBA            | teams                                       | https://api.balldontlie.io/v1/teams               | LIMITED  |           401 |             nan |                nan | Unauthorized or account tier does not include ... | 2026-09-19T19:39:14+00:00 |
| NBA            | games sample — 2025                         | https://api.balldontlie.io/v1/games               | LIMITED  |           401 |             nan |                nan | Unauthorized or account tier does not include ... | 2026-09-19T19:39:27+00:00 |
| NBA            | team season averages — optional access test | https://api.balldontlie.io/nba/v1/team_season_... | LIMITED  |           401 |             nan |                nan | Unauthorized or account tier does not include ... | 2026-09-19T19:40:45+00:00 |
| NFL            | teams                                       | https://api.balldontlie.io/nfl/v1/teams           | LIMITED  |           401 |             nan |                nan | Unauthorized or account tier does not include ... | 2026-09-19T19:40:58+00:00 |
| NFL            | games sample — 2025                         | https://api.balldontlie.io/nfl/v1/games           | LIMITED  |           401 |             nan |                nan | Unauthorized or account tier does not include ... | 2026-09-19T19:41:11+00:00 |
| NFL            | team season stats — access test             | https://api.balldontlie.io/nfl/v1/team_season_... | LIMITED  |           401 |             nan |                nan | Unauthorized or account tier does not include ... | 2026-09-19T19:42:29+00:00 |
| Premier League | games/match stats — 2025-26                 | https://www.football-data.co.uk/mmz4281/2526/E... | PASS     |           200 |             380 |                132 | nan                                               | 2026-09-19T19:42:30+00:00 |

## Pre-game data rule

Only information that would have been known before the target game begins may be used
as a predictor. Final scores and box/match statistics from an earlier game may be used for
a later game only after chronological shifting. Rolling calculations must use `shift(1)`
before the rolling window.

## Week 2 conclusion

1. NBA: use the established historical NBA collection workflow and derive chronological features.
2. NFL: use the established historical NFL collection workflow and derive chronological features.
3. Premier League: use Football-Data.co.uk historical season files.
4. Expected goals and historical player availability remain optional unless a reliable,
   timestamped source is confirmed.
