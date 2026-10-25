# Lab 1

**Name:**
**Due:** Sunday, October 25 at 11:59 PM
**Submit:** your repo URL in the Lab 1 assignment on CourseWorks

| Part | Where | File |
|---|---|---|
| **In class:** first DuckDB query on the penguins data | Session 1 | `notebooks/lab1_first_query.ipynb` |
| **At home:** two related tables of your own in DuckDB | Before Sunday | `notebooks/lab1_home_your_data.ipynb` |
| **At home:** lifecycle map of your data | Before Sunday | This file (below) |

---

## Lifecycle map of your data

In class we named five stages every data system has. Trace them for the two tables you loaded at home. Some rows ask what you did this week; the last two ask you to look ahead to the system you'll build by December. Educated guesses are fine; say where you're unsure.

**My tables:** Motor Vehicle Collisions - Crashes (main table) + 311 Service Requests from 2020 to Present (second table)

| Stage | For your data | Your answer |
|---|---|---|
| **1. Ingestion** | Where did each file come from, and how did you get it (portal download, export, API)? If the source changed its format tomorrow, what would break? | Both files came from the NYC Open Data portal. If the query function were removed, the datasets would be much larger and not contained to the specified years. But as long as the CSVs can still be downloaded, nothing should break. |
| **2. Validation** | What did `DESCRIBE`, `SUMMARIZE` and the key check reveal? Name one check you'd want to run *every time* new data arrives. | Summarize revealed multiple columns in the second table that are 100% null, which can be removed. The key check confirmed a good amount of overlap in zip codes. I would want to check for missing data in relevant columns every time new data arrives. |
| **3. Transformation** | What did you change to make the data usable (e.g. the missing-value fix)? What would you still need to clean, join or calculate to answer your question? | I changed the data type of the crash date in the maintable from VARCHAR to DATE, though this may not affect later calculations. I would still need to join the tablesto more efficiently answer questions related to incident counts of crash and speeding by zip codes. |
| **4. Scheduling** | How often does the source publish updates (check its website)? If your app used this data, how often would it need to refresh to stay useful, and why? | Both tables update daily, although the last update for the main table was June 15, 2026. Assuming daily updates, my app would need to refresh daily. |
| **5. Interface** | Who would want answers from this data? Write the plain-English question they'd ask, and what a good answer would show them. | Community boards, neighbors, and transportation safety advocates. "In my zip code in 2023, how many reports of speeding occurred and how many people were injured because of vehicle crashes?" "In [ZIP CODE] in 2023, there were [X] reports of speeding and [Y] people were injured because of vehicle crashes. Reported speeding and recorded crashes may not be related." |

**Which stage feels most fragile for your data, and why?** (two or three sentences)
The transformation stage seems the most fragile at the moment. It seems much of the main table's data is missing important information of where the crashes occurred. If the data cannot be cleaned or filled in utilizing information (like latitude and longitude) that does exist, about a third of the recorded crashes would be unusable and potentially not provide an accurate answer to an end user.

---

## Checklist before you submit

- [ ] In-class notebook: every cell ran, including your own query and three observations
- [ ] At-home notebook: both CSVs in `data/`, both tables loaded and checked, the key relationship described, five queries each with a one-line note, three observations, two dataset cards
- [ ] This lifecycle map filled in, plus the "most fragile" answer
- [ ] Every notebook saved (Cmd+S), then committed and pushed
- [ ] Repo URL pasted into CourseWorks
