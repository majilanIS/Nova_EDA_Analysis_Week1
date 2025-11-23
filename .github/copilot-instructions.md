## Repo Overview

- This repository is a small exploratory sentiment/EDA project built around a CSV dataset in `newsData/raw_analyst_ratings.csv` and interactive notebooks in `notebooks/` (notably `notebooks/nova_eda_task1.ipynb`).
- Lightweight package layout: `src/` contains library code, `scripts/` contains helper scripts, and `tests/` contains unit tests (unittest framework).

## Quick dev workflow

- Install dependencies: `pip install -r requirements.txt` (GitHub Actions uses Python 3.10).
- Run tests (local parity with CI): `python -m unittest discover -s tests`.
- Run notebooks interactively: start `jupyter lab` or execute a notebook non-interactively with `jupyter nbconvert --to notebook --execute notebooks/nova_eda_task1.ipynb`.

## CI / Test details

- The repository CI file `.github/workflows/unittests.yml` installs `requirements.txt` and runs `python -m unittest discover -s tests`. Use that exact command for local debugging to reproduce CI failures.
- CI uses Python 3.10 — prefer reproducing that runtime when investigating environment-specific issues.

## Important patterns & code locations (search here first)

- Notebooks: `notebooks/nova_eda_task1.ipynb` contains the main exploratory pipeline. It loads the CSV using a relative path `../newsData/raw_analyst_ratings.csv` — keep working directories consistent when running cells programmatically.
- Data: `newsData/` contains source CSV(s). Expect code to use relative file paths from `notebooks/` or scripts; adjust working directory when running from repo root versus notebook folder.
- Tests: `tests/` uses the standard library `unittest` (not pytest). Inspect `tests/` before editing test behavior.
- Scripts vs src: `scripts/` tends to hold runnable notebooks/scripts; `src/` should hold importable modules. Prefer adding reusable helpers to `src/` and small launchers to `scripts/`.

## Notebook-specific conventions & gotchas

- Cells in `nova_eda_task1.ipynb` perform data cleaning inline (e.g., publisher normalization, time-series resampling, LDA topic modeling). There are commented helper functions (e.g., `clean_text`, `normalize_publisher_name`) — check for commented implementations before adding replacements.
- Several notebook cells reference variables that may not be defined in the same cell (example: `n_topics` used for LDA). When converting notebook code into scripts or tests, ensure such globals are defined or passed explicitly.
- The notebook frequently casts and coerces `date` fields to `datetime` with `errors='coerce'` and UTC; follow the same approach when writing data-processing code to stay consistent with existing time handling.

## Search tips for an AI agent

- To find important helper functions / variables, search for these tokens: `clean_text`, `normalize_publisher_name`, `n_topics`, `publisher_normalized`, `raw_analyst_ratings.csv`.
- Reproduce CI locally with:

```
pip install -r requirements.txt
python -m unittest discover -s tests
```

## Editing guidance for AI code agents

- Preserve notebook order: many cells are incremental (load -> clean -> features -> analyze). If extracting code to `src/`, keep small, testable functions and add unit tests under `tests/`.
- Prefer non-destructive changes in notebooks: if you change a notebook cell, keep a backup or add a new cell that demonstrates the change.
- When adding new dependencies, update `requirements.txt` and ensure CI will still pass under Python 3.10.

## Integration & data flow notes

- Primary data flow is CSV -> pandas DataFrame -> cleaning/enrichment in notebooks/scripts -> analysis/plots. No external services or databases are used in the current tree.
- Visualizations rely on `matplotlib` / `seaborn` inline in notebooks; keep plotting code isolated from core logic when refactoring so tests don't depend on display output.

## Example micro-tasks for contributors (useful prompts)

- "Extract the headline cleaning pipeline from `notebooks/nova_eda_task1.ipynb` into `src/cleaning.py` as pure functions and add unit tests in `tests/test_cleaning.py`."
- "Convert the time-series resampling section into a function that accepts a DataFrame and returns daily/weekly/monthly counts; add test vectors."

## When uncertain, open these files first

- `notebooks/nova_eda_task1.ipynb` — exploratory pipeline and many code examples.
- `requirements.txt` — authoritative dependency list used by CI.
- `.github/workflows/unittests.yml` — reproduces CI runtime and commands.
- `newsData/raw_analyst_ratings.csv` — canonical input dataset used by notebooks.

If anything here is unclear or you want the instructions to emphasize different aspects (for example, how to run notebooks headlessly or how to structure new unit tests), tell me what to add or change and I will iterate.
