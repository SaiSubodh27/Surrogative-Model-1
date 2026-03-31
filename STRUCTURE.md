# Repository Structure Map

This document outlines the organization of the **Crystal Paradigm** repository and explains the intended contents of each directory to maintain a clean and scalable project layout.

## Folder Layout

```text
crystal_paradigm/
├── data/
│   ├── raw/                 # Original, immutable datasets (.csv, .cif files)
│   └── processed/           # Cleaned, standardized datasets ready for modeling
├── notebooks/
│   ├── 01_eda.ipynb         # Exploratory Data Analysis & visualization
│   ├── 02_feature_eng.ipynb # Pymatgen/M3GNet feature extraction experiments
│   └── 03_modeling.ipynb    # Model prototyping and Phase 1-4 evaluation
├── src/
│   ├── data_prep.py         # Modular scripts to clean and preprocess raw data
│   ├── features.py          # Functions to generate representations (CIF, M3GNet)
│   └── train.py             # Core logic for model training, ensembling, and cross-validation
├── models/                  # Serialized trained model checkpoints (e.g., .pkl files)
├── results/
│   ├── figures/             # Output plots (e.g., sse_results.png, feature_importance.png)
│   └── metrics/             # Saved performance reports, logs, and evaluation metrics
├── .gitignore               # Version control rules to ignore data, models, and temp files
├── requirements.txt         # Project dependencies for reproducibility
├── STRUCTURE.md             # This structural reference guide
└── README.md                # High-level overview, methodology, and results
```

## Guidelines for Use

1. **`data/`**: Never commit large `.csv` or `.zip` files to version control. Let scripts read from and write to this folder locally.
2. **`notebooks/`**: Treat notebooks as experimental scratchpads or tutorials. Move stable, reusable code to the `src/` directory.
3. **`src/`**: This is the application code. It should be modular and importable by the notebooks.
4. **`models/`**: For heavy trained models, keep them local. Avoid committing `.pkl` files.
5. **`results/`**: Output plots and CSVs of metrics go here.
