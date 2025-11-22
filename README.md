# Nova EDA Analysis — Week 1

**Project:** Exploratory data analysis and light sentiment/topic modeling over an analyst/news ratings CSV.

**Purpose:**

- Collect, clean, and explore `newsData/raw_analyst_ratings.csv` using interactive notebooks and small reusable modules.
- Provide a small, easy-to-run analysis pipeline suitable for experimentation and teaching data-cleaning / EDA patterns.

**Quick Links**

- Data: `newsData/raw_analyst_ratings.csv`
- Notebooks: `notebooks/nova_eda_task1.ipynb`
- Source helpers: `src/`
- Tests: `tests/`

**Requirements**

- Python 3.10 is recommended (CI uses 3.10).
- Install dependencies:

```bash
pip install -r requirements.txt
```

**How to run the analysis**

- Interactive (recommended for exploration):

```bash
jupyter lab
# open notebooks/nova_eda_task1.ipynb
```

- Headless (reproducible run of the notebook):

```bash
jupyter nbconvert --to notebook --execute notebooks/nova_eda_task1.ipynb
```

**Run tests**

- Tests use Python's `unittest`. From the repo root:

```bash
python -m unittest discover -s tests
```

**Data notes**

- The canonical dataset is `newsData/raw_analyst_ratings.csv`.
- Notebooks in this repo expect the file at `../newsData/raw_analyst_ratings.csv` when executed from within the `notebooks/` folder; when running from the repo root use `newsData/raw_analyst_ratings.csv`.
- Date fields in the notebook are parsed with `errors='coerce'` and treated as UTC where appropriate. When writing scripts, follow the same approach to preserve behavior.

**Repository layout**

- `newsData/` — CSVs and data resources.
- `notebooks/` — interactive Jupyter notebooks. See `notebooks/README.md` for details.
- `src/` — reusable code (data cleaning, feature extraction). See `src/README.md` for recommendations.
- `scripts/` — lightweight runnable helpers and scripts (if present).
- `tests/` — unit tests. See `tests/README.md` for test instructions.

**Development notes / recommendations**

- Prefer moving helper functions out of notebooks into `src/` so they can be unit tested.
- Keep functions small and explicit about input/output types. Use pandas DataFrames as the primary exchange format.
- When adding dependencies, update `requirements.txt` and ensure CI still passes under Python 3.10.

**CI**

- CI runs the tests using `python -m unittest discover -s tests`.
- Aim to keep the test suite small and deterministic.

**Next steps (suggested)**

- Add typed functions for the cleaning pipeline into `src/cleaning.py` and unit tests in `tests/test_cleaning.py`.
- Add a small `Makefile` or `tasks.json` for common commands (run tests, execute notebook).
- Add a short CONTRIBUTING guide if you expect outside contributors.

**Contact / Author**

- Repo owner: `majilanIS`
