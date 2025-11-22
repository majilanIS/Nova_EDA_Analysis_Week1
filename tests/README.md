# tests

This directory contains unit tests for the project. Tests use Python's built-in `unittest` framework.

Run tests

```bash
python -m unittest discover -s tests
```

Notes

- CI uses Python 3.10; prefer running tests in the same runtime to reproduce CI locally.
- Keep tests small and focused. When adding new functions to `src/`, add corresponding tests to `tests/`.
