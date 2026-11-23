# Findings report

Three things your data shows, each backed by one of your published tables.
Next week you'll ask your AI app these questions and check whether it gets the same answers.

## Finding 1

**What I found** (one or two sentences, with a number): Brooklyn had an average of 42.7 car crashes per day in the last month.

**From table:** `course.main.crashes_borough_summary`

**The query or row that shows it:**

```sql
borough	total_crashes	avg_per_day	pct_of_city	zip_codes_affected
BROOKLYN	1153	42.7	        33.9	        38

```

**A question a user could ask the app to discover this: What was the average number of car crashes in Brooklyn in the last month?

## Finding 2

**What I found:** There have been 6 deaths in NYC due to car crashes in the past 30 days.

**From table:** `course.main.crashes_deaths_top_zips`

**The query or row that shows it:**

```sql
zip_code	borough	total_fatalities	crashes
11101	        QUEENS	        1.0	        1
11203	        BROOKLYN	1.0	        1
11421	        QUEENS	        1.0      	1
10026	        MANHATTAN	1.0     	1
11214	        BROOKLYN	1.0     	1
11105	        QUEENS  	1.0     	1

```

**A question a user could ask the app to discover this:** How many people have died in NYC from car crashes in the last month?

## Finding 3

**What I found:** October 29th had 183 car crashes, the most of any day in the past month.

**From table:** `course.main.crashes_by_zip_day`

**The query or row that shows it:**

```sql
SELECT crash_date, sum(crashes)::INT AS crashes
FROM crashes_by_zip_day
GROUP BY crash_date
ORDER BY crashes DESC
```

**A question a user could ask the app to discover this:** What day in the last month had the most car crashes?

---

## What this data can't tell you

One limit a reader should know before trusting these findings (missing places, short time span, how values are collected): The data is limited to the last 30 days. The data is also limited to NYPD's reporting, which is "required to be filled out for collisions where someone is injured or killed, or where there is at least $1000 worth of damage." So it's possible that any crash that does not meet one of those three criteria could remain unreported.
