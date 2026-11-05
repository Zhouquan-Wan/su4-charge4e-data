# Quantum Charge-4e Superconductivity and Possible Deconfined Pseudocriticality in the Attractive SU(4) Hubbard Model

Processed QMC data and a standalone notebook for Fig. 2, 3, 5 and S6–S12 of this paper.

The notebook loads the figure data, performs the required transformations or
fits, and plots the results. PDFs and PNGs are saved in `figures/`.

- [data/](data/): 12 processed QMC CSV files, including ED benchmark references.
- [data/README.md](data/README.md): observables, units, errors, and analysis methods.
- [requirements.txt](requirements.txt): scientific packages and the Python notebook kernel.

For a first run, use Python 3.11 or 3.12.
Run these commands from the repository directory, with `python3` pointing to
one of those versions:

```bash
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
```

In VS Code:

1. Open the repository folder and install or enable the **Python** and **Jupyter** extensions.
2. Open [reproduce_all.ipynb](reproduce_all.ipynb), then choose **Select Kernel → Python Environments → .venv**.
3. Choose **Run All**.

The notebook plots the processed values and errors and recalculates
critical-exponent extrapolations, their envelopes, and the S8 finite-size gap
fits. Fig. 1 and S1–S5 are Feynman diagrams and schematics and are outside this
numerical figure reproduction package.
