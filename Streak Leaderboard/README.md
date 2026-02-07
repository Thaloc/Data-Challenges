# Streak Leaderboard (Active Streaks)

Compute the **active streak** per user from a lesson completions table and produce a leaderboard of the **top 10** users with the longest active streaks.

## Problem definition

- A **streak** is the number of **consecutive days** where the user completed **at least one** lesson.
- The drill sets **current date** to **2025-09-29**.
- A streak is considered **active** only if the user completed a lesson on **2025-09-28**.

## Input

**File:** `LessonStreaks.csv` (~900k rows)

Expected columns (names may vary):
- user identifier (e.g., `user_id`)
- completion date/time (e.g., `date` or `completed_at`)
- lesson id (not required for streak counting)

## Method

1. Load the CSV.
2. Normalize completion timestamps to a daily granularity:
   - `day = to_datetime(date_col).normalize()`
3. Keep dates `<= 2025-09-28` (the streak must end on this day).
4. De-duplicate to one row per `(user, day)` so multiple lessons on a day count once.
5. Compute consecutive-day runs per user using:
   - `rn = cumcount()` within each user (0..n-1)
   - `grp = day - rn days` (constant inside a consecutive run)
6. Aggregate each run to `(run_start, run_end, streak_len)`.
7. Keep only runs where `run_end == 2025-09-28` (active streaks).
8. Sort by `streak_len` descending to produce the top-10 leaderboard.

## Output

- `leaderboard`: top 10 users by `streak_len` (and their `run_start`, `run_end`)
- `third_longest_active_streak`: the length of the third longest active streak (submission answer)

## Run

```bash
pip install pandas
python your_script.py