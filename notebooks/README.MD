# notebooks

Interactive exploratory analysis is kept in this folder. Key notebook:

- `nova_eda_task1.ipynb` — main exploratory notebook that loads `newsData/raw_analyst_ratings.csv`, performs cleaning, resampling, and simple analysis (e.g., topic modeling and sentiment/EDA).

How to run

- Interactive: `jupyter lab` or `jupyter notebook` then open the notebook.
- Headless execution (reproducible run):

```bash
jupyter nbconvert --to notebook --execute notebooks/nova_eda_task1.ipynb
```

Data path note

- The notebook expects the data at `../newsData/raw_analyst_ratings.csv` when run from the repo root.

Notebook conventions

- The notebook converts date fields using `errors='coerce'` and uses UTC timestamps; preserve this behavior when converting code to scripts.
- Helper functions like `clean_text` and `normalize_publisher_name` may be defined inline; consider moving them into `src/` for reuse and testability.
