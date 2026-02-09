# README.md (Movie Metrics)

## Movie Metrics

Engineer user-level viewing metrics from Netflix activity logs.

### Task
For each user, compute:
- `first_finished_date`
- `first_finished_movie`
- `last_finished_date`
- `last_finished_movie`
- `movies_started`
- `movies_finished`

### Files
- `users.csv`  
  Required: `id`
- `activity.csv`  
  Required: `id`, `user_id`, `date`, `movie_name`, `finished`

### Method
- Convert `date` to datetime.
- Count starts and finishes per user.
- For first/last finished movie:
  - filter `finished == 1`
  - sort by `user_id`, `date`, `id` (tie-break)
  - take first/last row per user
- Merge results onto users.

### Output
A per-user table (`user_metrics`) with the engineered columns.

### Submission question
“How many users have **Fight Club** as the last film they’ve seen?”  
Computed as: `sum(last_finished_movie == "Fight Club")`.
