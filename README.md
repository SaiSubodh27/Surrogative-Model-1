# Crystal Paradigm: SSE Ionic Conductivity Surrogate Model

## Project Overview
Crystal Paradigm is a machine learning surrogate model designed to predict the ionic conductivity of Solid-State Electrolytes (SSE) for advanced battery applications. By predicting $\log(\text{min\_barrier})$ as a target variable, we derive the actual conductivity using the Arrhenius equation. This project leverages state-of-the-art materials informatics tools and deep learning embeddings to accelerate the discovery of high-performance SSE materials.

## Methodology
We employ a rigorous four-phase modeling strategy to capture hierarchical features from composition to 3D crystal structure:

- **Phase 1: Tabular & Baseline Modeling**  
  Establishing baseline performance using basic compositional and easily computable domain-specific tabular features.
- **Phase 2: CIF Structural Descriptors (Pymatgen)**  
  Integrating geometric, topological, and bonding environment descriptors extracted directly from Crystallographic Information Files (CIFs) using `pymatgen`.
- **Phase 3: Formula & Compositional Features**  
  Incorporating advanced stoichiometric and elemental properties to enrich the feature space independent of exact atomic coordinates.
- **Phase 4: M3GNet Graph Embeddings**  
  Leveraging pre-trained Materials 3D Graph Networks (M3GNet) to generate robust 64-dimensional latent embeddings, capturing the complex structural interactions within the crystal lattice.

## Performance
Our objective is to achieve a predictive accuracy with an **$R^2 > 0.90$** on unseen test datasets. To accomplish this, the project utilizes a Stacked Ensemble architecture combining powerful algorithms such as XGBoost and Random Forest, providing both high performance and interpretability.

## Visuals
### Model Performance
![Model Performance Placeholder](results/figures/sse_results.png)  
*Figure 1: Parity plot comparing predicted vs. experimental ionic conductivity.*

### Feature Importance
![Feature Importance Placeholder](results/figures/feature_importance.png)  
*Figure 2: SHAP summary plot illustrating the most influential features governing ionic conductivity.*

## Repository Structure Map

The repository is organized to cleanly separate source code, exploratory analysis, data, and outputs:

```text
crystal_paradigm/
├── data/
│   ├── raw/                 # Original, immutable data dumps
│   └── processed/           # Cleaned datasets ready for modeling
├── notebooks/
│   ├── 01_eda.ipynb         # Exploratory Data Analysis
│   ├── 02_feature_eng.ipynb # Feature extraction (Pymatgen, M3GNet)
│   └── 03_modeling.ipynb    # Training and ensembling the 4-Phase models
├── src/
│   ├── data_prep.py         # Scripts to clean and preprocess data
│   ├── features.py          # Feature extraction modules
│   └── train.py             # Model training pipelines
├── models/                  # Serialized model checkpoints (.pkl, etc.)
├── results/
│   ├── figures/             # Output plots (sse_results.png, etc.)
│   └── metrics/             # Evaluation metrics and logs
├── .gitignore               # Ignored files and directories
├── requirements.txt         # Project dependencies
└── README.md                # Project documentation
```
