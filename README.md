# Data Drills — Project Collection

A repository of small, self-contained analytics projects completed from Maven Analytics Data Drills. Each project focuses on a single objective using a provided dataset, with the goal of producing a clear, correct result and a reproducible workflow.

## What these projects are

- Short, scoped data challenges
- Dataset-driven, outcome-oriented
- Designed to practice core analytics patterns:
  - cleaning + validation
  - reshaping and deduplication
  - aggregation and ranking
  - time series logic (streaks, rolling windows)
  - joining and dimensional modeling basics
  - producing “submission-ready” answers

## Repository structure

Each drill has its own folder containing:
- A notebook (`.ipynb`) with an end-to-end solution
- A project-level `README.md` describing:
  - the objective
  - the dataset assumptions
  - the approach
  - outputs / key results
- Optional exported outputs (e.g., summary `.csv`)

Example layout:
```
drills/ <drill-name>/
solution.ipynb
README.md
outputs/
```

## Conventions used

- Deterministic logic (no manual steps required)
- Clear parameters at the top of notebooks (paths, “current date” if fixed by prompt, etc.)
- Defensive handling of common data issues:
  - multiple records per entity/day
  - missing or malformed dates
  - inconsistent labels
  - duplicate rows
- Outputs formatted as tables suitable for direct submission

## Typical deliverables

Depending on the drill, outputs may include:
- Aggregated tables (counts, sums, percent shares)
- Leaderboards/rankings (top N, ties handled explicitly)
- Derived metrics (streak lengths, retention measures, rolling stats)
- Exported result files (`.csv`) for verification

## Running the projects

- Install dependencies (commonly: `pandas`, `jupyter`)
- Place the dataset for each drill in the same folder as the notebook (or update `DATA_PATH`)
- Run all notebook cells to reproduce results
