Purpose
-------
This file gives concise, actionable guidance to AI coding agents working in this repository so they become productive quickly.

Repository snapshot
-------------------
- Root README: [README.md](README.md)
- Course material and notebooks: `kmooc/` (e.g. [kmooc/sogang-ml-dl/personal-study/knn_example.ipynb](kmooc/sogang-ml-dl/personal-study/knn_example.ipynb)).

Quick overview (big picture)
-----------------------------
- The repo is primarily a collection of Jupyter notebooks used as study notes and examples (no web service or build system).
- Notebooks live under `kmooc/...` grouped by course; edits should respect the notebook-first workflow.

Developer workflows & commands
-----------------------------
- Create and activate a Python venv, then install minimal dependencies inferred from imports:

```bash
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install numpy scikit-learn jupyter
```

- Start interactive work:

```bash
jupyter lab  # or `jupyter notebook`
```

- Run a notebook headlessly (useful for CI or reproducing outputs):

```bash
jupyter nbconvert --to notebook --execute \
  kmooc/sogang-ml-dl/personal-study/knn_example.ipynb \
  --ExecutePreprocessor.timeout=600 --output executed_knn.ipynb
```

Project-specific conventions & patterns
-------------------------------------
- Notebooks are the primary source files. Keep cells' `metadata.language` set (e.g. `python`) when programmatically editing cells.
- Many notebooks include Korean comments and printed outputs — preserve language/commenting style when editing unless asked otherwise.
- Code examples use common ML imports (e.g. `numpy`, `sklearn`, `sklearn.preprocessing`) — infer missing dependencies from notebook imports.
- Example pattern: `knn_example.ipynb` defines small helper functions (e.g. `cal_Eculiden_dist`, `majority_vote`) inside notebook cells rather than separate modules.

Integration points & external dependencies
------------------------------------------
- Primary runtime dependencies are Python packages used in notebooks: `numpy`, `scikit-learn`, and `jupyter`.
- There is no detected CI, package manifest, or test harness — assume manual execution via Jupyter.

Editing and commit guidance
--------------------------
- For small algorithm or text fixes, edit the notebook cell directly and keep outputs if they help understanding; ask the repo owner whether they prefer cleaned notebooks (no outputs) before mass commits.
- If you refactor reusable code out of notebooks, create a small module under a new `src/` or `tools/` directory and update the notebook to import it.
- Keep commits small and focused: change one notebook or add one helper script per commit.

What an AI agent should do first
-------------------------------
1. Open `kmooc/sogang-ml-dl/personal-study/knn_example.ipynb` to learn the project's tone and conventions (Korean comments, inline helper functions).
2. Create a virtualenv and install `numpy scikit-learn jupyter` before running or editing notebooks.
3. If asked to run notebooks programmatically, use `jupyter nbconvert --execute` with an increased timeout.

If anything is unclear
----------------------
- Ask the repo owner whether they want notebooks committed with outputs or stripped, and whether they'd prefer extracted helper code to live in `src/`.
