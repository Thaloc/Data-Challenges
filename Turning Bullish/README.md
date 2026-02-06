# README.md

## Project: SPY Golden Cross Detector

Compute 50-day and 200-day moving averages for SPY closing prices and flag Golden Cross crossover dates.

### Files
- `SPY_close_price_5Y.csv` — input dataset (must contain `Date` and `Close` columns).
- `golden_cross.py` (optional) — script version of the notebook logic.
- `SPY_moving_averages_golden_cross.csv` — output table (generated).

### Requirements
- Python 3.9+ recommended
- `pandas`, `numpy`

Install:
```bash
pip install pandas numpy