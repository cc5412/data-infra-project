# Lab 2 · Reflection

**Name:**
**Due:** Sunday, November 8 at 11:59 PM

Answer in a few sentences each. Specific beats long.

**1. Your join.** Which column connected your two tables? How many rows went in, how many came out, and what did you do about anything that didn't match?
The zip code column connected the two cleaned tables, which were aggregated by zip. 225 rows (from table A which had more rows) went in and 171 rows came out when I did a join. In order to retain zip codes that may have not appeared in one of the two tables, I did a full join. This resulted in 225 rows out, meaning all of the table B zip codes were already listed within table A.

**2. The reading.** Kleppmann describes tables (relational), documents (nested, like JSON) and graphs as different ways to model data. Would any of your two tables have been easier to work with as a document or a graph? Why or why not?
Neither table would have been easier to work with as a document or a graph. The document model is better for self-contained documents and would have complicated the join. The graph model might have helped in joining using zip code and having a relation of coordinates to street address and borough, but likely overkill as it's meant for data where everything relates to everything. The relational model remains best for structured, normalized data requiring joins and consistency.

---

**Checklist before you submit**

- [x] `notebooks/lab2_joins.ipynb`: Part A run in class, Part B completed with your own tables
- [x] Every Part B text cell filled in (grain, unmatched rows, what the result tells you)
- [x] This file answered
- [x] Notebook saved (Cmd+S), then committed and pushed
- [x] Repo URL submitted on CourseWorks
