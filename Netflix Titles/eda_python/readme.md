# 📺 Netflix Titles — EDA (Python)

A beginner-friendly exploratory data analysis of the Netflix Movies & TV Shows dataset using **Python (Pandas + Matplotlib/Seaborn)**.  
This folder contains the cleaning notebook, the cleaned dataset used for visualization, and screenshots of the main charts.

---

## Project files (this folder)
- `netflix_titles.csv` — original dataset (raw)
- `cleaned_netflix_data.csv` — cleaned dataset (used for visualization)
- `netflix_eda.ipynb` — Jupyter notebook with cleaning & plots
- `visuals/` — exported plot images (screenshots used below)
  - `type_distribution.png`
  - `movie_duration_hist.png`
  - `tv_season_count.png`
  - `avg_duration_top_5_country.png`
  - `boxplot_rating.png`
  - `pie_rating.png`
  - `era_distribution.png`
  - `...` (other images)

---

## Quick start
1. Open `netflix_eda.ipynb` in Jupyter.
2. The notebook expects the raw file `netflix_titles.csv` in the same folder (or change the path at the top).
3. (Optional) Create and activate a venv, then install dependencies:
```bash```
pip install -r requirements.txt
4. Run the notebook cells to reproduce cleaning steps and visuals.
5. `cleaned_netflix_data.csv` is already exported if you want to use it in Power BI.

---

## Visuals (screenshots)
> All images are in the `visuals/` folder. (If you rename images locally, update the links below.)

| Plot | Description |
|---|---|
| ![type_distribution](visuals/type_distribution.png) | **Count of Movies vs TV Shows** — shows overall composition. |
| ![movie_duration_hist](visuals/movie_duration_hist.png) | **Distribution of Movie Durations** — histogram with avg line (~99.6 min). |
| ![tv_season_count](visuals/tv_season_count.png) | **Distribution of TV Show Seasons** — most shows have 1–2 seasons. |
| ![avg_duration_top_5_country](visuals/avg_duration_top5_country.png) | **Avg Movie Duration — Top 5 countries** (by average runtime). |
| ![boxplot_rating](visuals/boxplot_rating.png) | **Movie Duration by Rating** — boxplots highlighting spread / outliers. |
| ![pie_rating](visuals/pie_rating.png) | **Top 5 Ratings (Movies)** — share of dominant rating categories. |
| ![era_distribution](visuals/era_distribution.png) | **Content Count by Era & Type** — Classic / Old School / Modern counts. |

---

## Data cleaning highlights
- - Removed rows with missing `date_added` (kept only rows with valid `date_added`).

  - **Note:** An accidental helper column (`date_time`) was created during conversion and later removed — this was an unintended step fixed in the notebook.
- Filled missing text fields with friendly defaults:
  - `director`, `cast` → `"Not Available"`
  - `country` → `"Unknown"`
  - `rating`, `duration` → `"Unknown"`
- Extracted numeric and text parts from `duration`:
  - `duration_int` (e.g., 90)
  - `duration_type` (e.g., `min`, `Season`)
- Converted `date_added` to datetime (used `errors='coerce'` to safely parse).
- Created `platform_era` derived column from `release_year`:
  - `Classic` ( < 1990), `Old School` (1990–2009), `Modern` (>=2010)

---

## Key insights (short)
- **Modern era dominates** the catalogue; most items are from recent years.
- **Movies outnumber TV shows**, but TV shows grow in recent years.
- **Average movie runtime ≈ 100 minutes.**
- **Most TV shows have 1–2 seasons** (distribution heavily skewed to short series).
- **Top ratings** are dominated by `TV-MA` and `TV-14` categories.

(For a longer, personal summary see `KEY_INSIGHTS.md`.)

---

## Notes & reproducibility
- The notebook includes inline comments explaining each step (why I filled some missing values, why I removed others, regex usage for duration).
- If you want to reproduce visuals exactly, use the same Python environment:
  - `pandas`, `numpy`, `matplotlib`, `seaborn`
- I recommend adding a `requirements.txt` if you want to pin versions.

---

## Data source
- Kaggle: *Netflix Movies and TV Shows* (source link used during the project)

---

## License / Use
This project is for learning and portfolio purposes. If you reuse or publish visuals, please credit the original dataset.
