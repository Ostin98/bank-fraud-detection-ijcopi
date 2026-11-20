# Bank Fraud Detection with Neural Networks and Branch-and-Bound Nearest-Neighbour Search

Code and experiments for the paper:

> A. Ferreyra-Ramírez, O. U. Martínez-Campos, E. Rodríguez-Martínez and C. Avilés-Cruz,
> *"Bank Fraud Detection with Neural Networks and an Empirical Analysis of Branch-and-Bound
> Nearest-Neighbour Search Efficiency under Growing Dimensionality"*,
> International Journal of Combinatorial Optimization Problems and Informatics (IJCOPI), 2027.
> Extended version of the paper presented at MCPR 2026.

Universidad Autónoma Metropolitana, Unidad Azcapotzalco.

---

## Overview

This repository contains the complete pipeline used in the paper:

1. A comparison of supervised and unsupervised neural families (regularised MLP, 1-D CNN
   and a convolutional autoencoder) for credit-card fraud detection on the public **ULB**
   benchmark, evaluated with threshold-independent measures (AUC-ROC, AUC-PR) under a
   genuine 0.17 % fraud rate.
2. An empirical study relating the **dimensionality** of the feature representation both to
   exact nearest-neighbour search cost (k-d tree and ball tree vs. brute force) and to
   detection quality, identifying the region where detection is near its best while tree
   pruning still reduces query time.

## Repository structure

```
.
├── notebooks/
│   ├── 01_preprocesamiento.ipynb   # Feature engineering (8 numerical features) and splits
│   ├── 02_knn_bb.ipynb             # k-NN + branch-and-bound (k-d tree vs brute force)
│   ├── 02b_knn_ball_tree.ipynb     # Ball-tree search benchmark
│   ├── 03_mlp.ipynb                # Regularised MLP (5 runs, mean ± std)
│   ├── 04_cnn.ipynb                # 1-D CNN (5 runs, mean ± std)
│   ├── 05_autoencoder.ipynb        # Convolutional autoencoder
│   ├── 05b_histograma.ipynb        # Reconstruction-error histograms
│   ├── 06_tabla_final.ipynb        # Aggregates runs into the results tables
│   └── 07_arbol_bb.ipynb           # Pruning visualisation (branch and bound)
├── results/                        # Pre-computed metrics to reproduce tables and figures
│   ├── benchmark_dimensionalidad.csv
│   ├── benchmark_completo.csv
│   ├── metricas_por_corrida.csv
│   └── tabla_comparativa.csv
├── data/                           # Datasets are NOT included — see data/README.md
├── requirements.txt
└── README.md
```

## Requirements

- Python 3.10+
- See `requirements.txt` (NumPy, scikit-learn, TensorFlow/Keras, matplotlib)

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Data

The datasets are **not** distributed with this repository (see `data/README.md`):

- **ULB credit-card fraud dataset** (public): download `creditcard.csv` from
  [Kaggle](https://www.kaggle.com/mlg-ulb/creditcardfraud) and place it in `data/`.
- **Proprietary bank dataset** (`bank.xlsx`): not shared, as it contains confidential
  transaction records. The preprocessing in `01_preprocesamiento.ipynb` documents the
  eight engineered features so the pipeline can be applied to an equivalent dataset.

## Reproducing the results

Run the notebooks in order. `01` builds the engineered features and the train/test/validation
splits (80/20 train/test and, within the training set, a further 90/10 train/validation split,
stratified). The neural notebooks (`03`–`05`) repeat training over five independent runs with
fixed seeds and report mean ± standard deviation; `06` aggregates them into the results tables.
The k-NN / tree notebooks (`02`, `02b`, `07`) produce the search-efficiency and
detection-vs-dimensionality benchmarks. The `results/` CSVs let you regenerate the tables and
figures without re-running the full training.

## Citation

```bibtex
@article{ferreyra2027bankfraud,
  title   = {Bank Fraud Detection with Neural Networks and an Empirical Analysis of
             Branch-and-Bound Nearest-Neighbour Search Efficiency under Growing Dimensionality},
  author  = {Ferreyra-Ram{\'i}rez, Andr{\'e}s and Mart{\'i}nez-Campos, Ostin Uriel and
             Rodr{\'i}guez-Mart{\'i}nez, Eduardo and Avil{\'e}s-Cruz, Carlos},
  journal = {International Journal of Combinatorial Optimization Problems and Informatics (IJCOPI)},
  year    = {2027}
}
```

## License

To be defined by the authors before publication (e.g. MIT for the code). The proprietary
dataset is excluded and remains confidential.
