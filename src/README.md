# src

This directory contains importable library code for the project. Keep reusable data-processing and cleaning functions here so notebooks and scripts can import them.

Suggested contents

- `cleaning.py` — text cleaning helpers (e.g. `clean_text`, `normalize_publisher_name`).
- `timeseries.py` — functions for resampling and aggregating time-series data.
- `features.py` — feature extraction (sentiment, topic features, etc.).

Development notes

- Write small, well-tested functions that accept and return pandas DataFrames (avoid notebook-specific side-effects).
- When adding modules, keep docstrings and typing hints for clarity.

Importing

- From repo root you can import modules like:

```python
from src import cleaning
```

If you plan to make the package installable, add packaging metadata (e.g., `pyproject.toml` or `setup.cfg`).
