# newsData

This folder contains the dataset(s) used by the notebooks and scripts in this repository.

Primary file

- `raw_analyst_ratings.csv` — canonical input dataset used by `notebooks/nova_eda_task1.ipynb`.

Usage

- Load with pandas:

```python
import pandas as pd
df = pd.read_csv('newsData/raw_analyst_ratings.csv')
```

Notes and assumptions

- The notebook converts date fields with `errors='coerce'` and uses UTC where appropriate; follow the same approach when writing scripts.
- Keep the CSV in this folder (or update notebook/script relative paths) so cells and scripts load data consistently.

Contact

- See project root `README.md` for overall project context and next steps.
