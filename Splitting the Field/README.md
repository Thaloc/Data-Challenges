# 2025 MLB Position Counts

Count how many **unique players** qualify at each position in the 2025 MLB season.

A player can qualify at multiple positions; they are counted **once per position**.

## Dataset

**Input file:** `baseball_positions.csv`

**Required columns:**
- `Name` — player name
- `Team` — team abbreviation (may be multiple rows per player if traded)
- `Position` — one or more qualified positions (often delimited, e.g. `OF/DH`)

**Qualification rule (assumed already applied in the dataset):**
- Fielding position: started **≥ 20** games at that position
- Pitcher: started **≥ 5** games as a pitcher

## Method

1. Load the CSV with pandas
2. Split `Position` on common delimiters (`/`, `,`, `;`, `|`)
3. Explode to one row per `(Name, Position)`
4. De-duplicate `(Name, Position)` to avoid double-counting multi-team rows
5. Group by position and count distinct players
6. Sort counts descending (ties broken alphabetically)

## Output

A table with:
- `Position_clean` — position label
- `player_count` — number of unique players qualifying at that position