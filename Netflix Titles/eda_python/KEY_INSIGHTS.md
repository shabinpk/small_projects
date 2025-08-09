# Netflix EDA — Personal Summary & Notes

**Project purpose:** practice data cleaning, feature extraction, and basic EDA with Python; produce visuals useful for a dashboard.

## Quick facts
- Raw rows processed: ~8k (after initial date filtering and duration filtering)
- Main numeric columns used: `duration_int`, `season_count` (extracted)
- New columns created: `duration_int`, `duration_type`, `season_count`, `platform_era`

## What I did (detailed)
1. Loaded dataset and checked duplicates / nulls.
2. Dropped rows missing `date_added` (reason: needed to parse and build `platform_era`).
3. Replaced missing object fields (`director`, `cast`, `country`, `rating`, `duration`) with `"Not Available"` / `"Unknown"` to avoid dropping too many rows.
4. Used `str.extract(r'(\d+)\s*(\w+)')` to create `duration_int` and `duration_type`.
5. Removed rows where `duration_int` was missing (these rows could not be used for duration-based analysis).
6. Converted `date_added` to datetime using `pd.to_datetime(..., errors='coerce')` and dropped `NaT`s.
7. Saved cleaned CSV for Power BI, and produced Python visuals.

## Key quantitative takeaways
- **Average movie duration:** ~100 minutes
- **TV shows:** most have 1–2 seasons (mean ~1.8)
- **Content era:** Modern era is by far largest; classic titles are few
- **Ratings:** `TV-MA` and `TV-14` are the most common top ratings among movies (dominant categories)

## Improvements / future work
- Standardize `country` (split multiple-country entries and pick primary country or explode rows).
- Keep missing `director` and `cast` as "Unknown" is okay for now, but later consider `explode` and link to external databases for enrichment.
- For duration: unify units (min vs season) more explicitly and keep separate tables for movie durations vs TV seasons.
- For reproducible environment, add `requirements.txt` with package versions.
- Add a polished set of visuals (Plotly for interactivity) for the portfolio page.

## One-line summary to use on LinkedIn/Git
“Performed EDA on Netflix Titles (8k+ rows): cleaned and extracted runtime/season features, visualized duration and era trends, and prepared a Power BI dashboard. (Py + Power BI)”

