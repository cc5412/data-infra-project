# Data dictionary

This file describes the tables your pipeline publishes. Copy the Columns section once per table. In Session 5, an AI model will read it to write SQL against your data, so a clear description here means better answers there. Write it for a smart reader who has never seen your data.

## The table

**Table name on MotherDuck:** `course.main.car_crashes`

**One row is:** (the grain, e.g. "one country in one year") 
One row is a motor vehicle collision as reported by the NYPD.

**Source:** (API name and link to its documentation)
Motor Vehicle Collisions - Crashes
Documentation: https://dev.socrata.com/foundry/data.cityofnewyork.us/h9gi-nx95
Request URL: https://data.cityofnewyork.us/resource/h9gi-nx95.json

**Refreshed:** (e.g. "daily at 6 AM New York time by GitHub Actions; a full snapshot of the last 14 days")
Daily at 11:17 UTC (about 6 AM in New York by GitHub Actions. It captures data from the last 30 days.

**Removed on purpose:** (rows the pipeline drops, and why, e.g. "regions like 'World', so averages count countries only")
Zip codes that are 'unspecified.'

## Columns

| Column | Type | What it means | Units or allowed values | Example |
|---|---|---|---|---|
| crash_date | datetime64[us]| date of the car crash| dates (YYYY-MM-DD)| 2026-10-08 |
| borough    | str| NYC borough| BRONX, BROOKLYN, MANHATTAN, QUEENS, STATEN ISLAND, or NULL| BROOKLYN|
|  zip_code  | str| 5-digit zip code| 5-digit zip code within NYC ranges (plus a few from Long Island)| 11207|
| latitude        | float64| Y coordinate| Decimal that is appropriate for NYC area.| 40.660378|
| longitude                | float64 | X coordinate | Negative decimal that is appropriate for NYC area. | -73.895020  |
| number_of persons_injured                         | int64        | Count of people injured in the car crash.             | Integer >= 0                                                   | 1            |
| number_of persons_killed                                                  | int64        | Count of people killed in the car crash.             | Integer >= 0                                                    | 0            |
| number_of pedestrians_killed                                                                          | int64        | Count of pedestrians killed in the car crash.             | Integer >= 0                                                   | 2            |
| number_of cyclist_killed                                                                                                      | int64        | Count of cyclists killed in the car crash.             | Integer >= 0                                                   | 3            |
| number_of motorist_killed                                                                                                                              | int64        | Count of people in the car killed in the car crash.             | Integer >= 0                                                   | 1            |
| collection_id                                                                                                                                                       | str        | Unique identified for reported crash events.             | A long string of jumbled numbers and letters.                                                   | c901103dccb4b9bd9b3e31e5e16be503            |
| on_street_name                                                                                                                                                                    | str        | Name of the street on which the crash occurred.             | Street names, meaning full words.                                                   | 47 STREET            |


## What this data can't tell you

(2–3 limits: years not covered, places missing, how values are estimated, anything a user might wrongly assume)

Car crashes beyond the last 30 days. The reason for the car crash. The time of the crashes.

## Example questions it can answer

1. What day in the last month had the most (or least) deaths due to car crashes in NYC?
2. What borough had the most car crashes in the last 30 days?
3. What zip codes had bikers die in car crashes in the last 30 days?
