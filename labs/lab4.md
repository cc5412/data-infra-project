# Labs 3 + 4 · Pipeline submission

**Name:**
**Due:** Sunday, November 22 at 11:59 PM

## Links

**A successful run of your pipeline** (Actions tab → the green run → copy the address): https://github.com/cc5412/data-infra-project/actions/runs/45150317036
**A deliberately failed run** (Run workflow with "Break the data on purpose" ticked → the red run → copy the address): https://github.com/cc5412/data-infra-project/actions/runs/45151424150

**Your table on MotherDuck:** `course.main.car_crashes`

## Reflections

Answer in a few sentences each. Specific beats long.

**1. Your checks.** Which of your checks would you be most worried to see fail, and what would go wrong for a user of your app if bad data got through?
I am most concerned about the ZIP code check because some car crashes outside the recent date range are from outside NYC. This could likely happen again. If bad data went through, the NYC crash count would be inflated with numbers from outside the city. Although, the bigger issue might be the pipeline failing and an end user not being able to USE the data rather than a single crash from a non-NYC zip code affecting much.

**2. Run it twice.** What happens to your MotherDuck table if your pipeline runs twice in one day? How do you know?
The table should not change because the dataset is updated daily and is not a live stream. If a second update is pushed on NYC Open Data, a second run of the pipeline would capture this and replace the MotherDuck table with the newly published data. Also, the newly generated table is entirely new and does not append anything. I know this because of how pipeline.py is written.

**3. Your schedule.** How often does your source actually update? Is daily the right schedule for it, and would you take a full copy or only what's new?
The source dataset updates daily. That is a good schedule since crashes can happen at any time of day, but also because I decided to remove times from my pipeline. It's best to take a full copy in case crashes are reported days later after they occur.

**4. What leaves your control.** Next week an AI model will see your table's description and users' questions. Is there anything in your data, or anything a user might type, that shouldn't be sent to a free AI service? Why or why not?

I cannot think of anything that would not be OK for a free AI service to see. The data is publicly available and the tables and questions do not include any personal information, token info, or propietary data

---

## Set up your secrets (once)

Your MotherDuck token is a password. It goes in two secret stores, **never** in a file, a notebook, or an AI chat.

**Get a token:** app.motherduck.com → your name (bottom left) → **Settings** → **Access Tokens** → **Create token**. Name it `codespaces`. Copy it.

**A. For your Codespace** (so `python pipeline.py` can publish):
github.com → your profile picture → **Settings** → **Codespaces** → **New secret**. Name `MOTHERDUCK_TOKEN`, paste the token, choose your course repo under **Repository access**, **Add secret**. Then restart your Codespace.

**B. For GitHub Actions** (so the daily run can publish):
your course repo on github.com → **Settings** (repo tab, not your profile) → **Secrets and variables** → **Actions** → **New repository secret**. Name `MOTHERDUCK_TOKEN`, paste the same token, **Add secret**.

If a token ever leaks, delete it in MotherDuck right away and make a new one (then update both secrets).

---

**Checklist before you submit**

- [x] `project.toml` points to **your** API, with at least five checks of your own (each with a why) and at least three tables: one clean table and at least two analysis tables (trend, key metrics or ranking)
- [x] `docs/findings.md`: three findings, each backed by one of your tables
- [x] A green run and a red run on the Actions tab, both linked above
- [x] `docs/data_dictionary.md` filled in for every table you publish
- [x] This file answered
- [x] No token anywhere in your files (tokens start with `eyJ`: search your repo with Cmd+Shift+F)
- [x] Committed and pushed; repo URL submitted on CourseWorks
