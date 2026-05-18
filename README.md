# Spatiotemporal Signal Propagation Analysis

## Project Description

This project investigates spatiotemporal signal propagation in epithelial cell populations using graph-based analysis of single-cell signaling dynamics.

The analysis focuses on how different PI3K-AKT pathway mutations influence intercellular signaling coordination, propagation timescales, and robustness of the Relative Risk (RR) metric across different analytical parameters.

---

## Repository Structure

```text
repo-root/
│
├── notebooks/
│   ├── TaskA1_MutationComparison.ipynb
│   ├── TaskA2_LaggedExposure.ipynb
│   ├── TaskA3_ParameterRobustness.ipynb
│   └── TaskB_PropagationStrengthDecay.ipynb
│
├── outputs/
│   ├── comparison_mutation_ERKKTR_ratio/
│   ├── exp_1_site_1_ERKKTR_ratio/
│   ├── exp_1_site_5_ERKKTR_ratio/
│   ├── exp_1_site_9_ERKKTR_ratio/
│   ├── exp_1_site_13_ERKKTR_ratio/
│   ├── exp_1_site_17_ERKKTR_ratio/
│   ├── sweep_r30/
│   ├── sweep_r90/
│   ├── sweep_r150/
│   ├── mutations_comparison_table.csv
│   ├── lagged_exposure_table.csv
│   ├── lagged_exposure_analysis.png
│   ├── lagged_exposure_plot_AKT_PTEN.png
│   ├── parameter_robustness_radius.png
│   └── A3_full_parameter_sweep_r.csv
│
├── scripts/
│   ├── compare_spatiotemporal_behavior.py
│   ├── spatiotemporal_signal_propagation.py
│   ├── 01-readme-experiment-description_2022-04-05.csv
│   └── __pycache__/
│
├── Project2Report.pdf
│
└── README.md
```

---

## Environment Setup

- Python 3.12 or newer is recommended.
- Install the required scientific Python packages manually if needed.

Suggested packages:

```bash
pip install pandas numpy matplotlib seaborn scipy networkx jupyter nbconvert
```

Optional: create a virtual environment before installation.

```bash
python -m venv venv

# Linux / macOS
source venv/bin/activate

# Windows
venv\Scripts\activate
```

---

## Reproducing the Analysis

All analyses can be executed directly inside Jupyter Notebook / VS Code or from the terminal using `nbconvert`.

---

## Task A1 — Multi-Mutation Spatiotemporal Comparison

Research question:

> Do different PI3K-AKT pathway mutations alter the strength of spatiotemporal signal propagation?

Run:

```bash
jupyter nbconvert --to notebook --execute notebooks/TaskA1_MutationComparison.ipynb
```

Outputs:

- `mutations_comparison_table.csv`
- `mutations_barplot.png`

This notebook:

- compares WT and mutant cell lines,
- computes Relative Risk (RR),
- performs Mann–Whitney U statistical testing,
- applies Bonferroni correction,
- generates comparison visualizations.

---

## Task A2 — Lagged Exposure Analysis

Research question:

> Do different mutations exhibit different spatiotemporal relay timescales?

Run:

```bash
jupyter nbconvert --to notebook --execute notebooks/TaskA2_LaggedExposure.ipynb
```

Outputs:

- `lagged_exposure_table.csv`
- `lagged_exposure_plot.png`

This notebook:

- computes lagged Relative Risk RR(τ),
- evaluates propagation delays across mutations,
- identifies optimal lag τ*,
- visualizes signaling propagation timescales.

---

## Task A3 — Parameter Robustness Assessment

Research question:

> How sensitive is the Relative Risk metric to parameter selection?

Run:

```bash
jupyter nbconvert --to notebook --execute notebooks/TaskA3_ParameterRobustness.ipynb
```

Outputs:

- `parameter_robustness_radius.png`
- `parameter_sweep_results.csv`

This notebook:

- evaluates RR stability across parameter sweeps,
- compares different spatial radii or temporal windows,
- recommends biologically meaningful parameters.

---

## Part B — Independent Research

The repository also contains an independent research notebook:

Research question:
> How does propagation strength decrease with graph distance? Does the decay differ in WT vs mutants?

Run: 

```bash
jupyter nbconvert --to notebook --execute notebooks/TaskB_PropagationStrengthDecay.ipynb
```

This notebook: 

- defines graph distances (d) as shortest-path steps in the cell neighbor graph
- detects whether neighbors at distance d show jump events
- measures whether this exposure increases probability of future jump
- computes propagation strength using Relative Risk (RR)
- compares RR decay across distances for WT vs mutants
- visualizes how signaling propagation decreases with graph distance

---

## Notes

- All analyses should be reproducible directly from the notebooks.
- Outputs are saved into the `outputs/` directory.
- Figures and tables generated in the notebooks are used in the final PDF report.
