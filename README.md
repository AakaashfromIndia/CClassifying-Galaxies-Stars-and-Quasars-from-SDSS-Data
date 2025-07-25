# Classifying Galaxies, Stars, and Quasars from SDSS Data

Comparison of several machine learning models for the automated classification of celestial objects - galaxies, stars, and quasi-stellar objects (QSOs) using data obtained from the Sloan Digital Sky Survey (SDSS). It aims to enhance astrophysical classification by applying a data-driven approach and evaluating various algorithms for performance and accuracy.

## Overview

- **Goal:** Distinguish between galaxies, stars, and quasars using supervised machine learning techniques.
- **Data Source:** Sloan Digital Sky Survey (SDSS) DR16 Spectroscopic and Photometric data.
- **Models Compared:**
  - Decision Tree
  - Random Forest
  - Support Vector Machine (SVM)
  - K-Nearest Neighbors (KNN)
  - Logistic Regression
  - Naive Bayes
  - Multi-Layer Perceptron (MLP)
  - Gradient Boosting (including LightGBM and Extreme Gradient Boosting)

## Dataset

The dataset was obtained by running the following SQL query on the [SDSS SkyServer DR16](http://skyserver.sdss.org/dr16/en/tools/search/sql.aspx):

```sql
SELECT TOP 500000
  p.objid, p.ra, p.dec, p.u, p.g, p.r, p.i, p.z,
  p.run, p.rerun, p.camcol, p.field,
  s.specobjid, s.class, s.z AS redshift,
  s.plate, s.mjd, s.fiberid
FROM PhotoObj AS p
JOIN SpecObj AS s ON s.bestobjid = p.objid
WHERE
  p.u BETWEEN 0 AND 19.6
  AND p.g BETWEEN 0 AND 20
```

- **Number of samples:** 500,000 (with representative coverage across classes)
- **Features:** Includes photometric bands (u, g, r, i, z), object positions (ra, dec), spectroscopic redshift, and categorical labels.

## Repository Structure

| File | Description |
|------|-------------|
| Decision_Tree.ipynb / decision_tree.py | Decision Tree model notebook/script |
| Random_Forest.ipynb / random_forest.py | Random Forest classifier |
| SVM.ipynb / svm.py | Support Vector Machine implementation |
| KNN.ipynb / knn.py | K-Nearest Neighbors classifier |
| Gradient_boost.ipynb / gradient_boost.py | Gradient Boosting (scikit-learn) |
| LightGBM.ipynb / lightgbm.py | Light Gradient Boosted Machine classifier |
| Extreme GB.ipynb / Extreme GB.py | Extreme Gradient Boosting (XGBoost) |
| Logistic_Regression.ipynb / logistic_regression.py | Logistic Regression model |
| Naive_bayes.ipynb / naive_bayes.py | Naive Bayes classifier |
| MLP.ipynb / mlp.py | Multi-Layer Perceptron (Neural Net) |
| README.md | Project documentation |

## Notebooks and Scripts

Each notebook/script includes:
- Data preprocessing and feature selection.
- Model training, cross-validation, and evaluation.
- Performance comparison metrics (accuracy, confusion matrix, etc.).
- Visualization of classification results.

You may run the `.ipynb` notebooks interactively or use the corresponding `.py` files for batch runs.

## Getting Started

1. **Clone this repository:**
   ```bash
   git clone https://github.com/AakaashfromIndia/Classifying-Galaxies-Stars-and-Quasars-from-SDSS-Data.git
   cd Classifying-Galaxies-Stars-and-Quasars-from-SDSS-Data
   ```

2. **Install requirements:**  
   Each notebook or script specifies its dependencies (primarily `scikit-learn`, `lightgbm`, `xgboost`, and data analysis libraries).  
   Install them via `pip`:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run or explore Jupyter notebooks:**  
   ```bash
   jupyter notebook
   ```
   or, execute scripts:
   ```bash
   python decision_tree.py
   ```

## Model Comparison

The repository demonstrates side-by-side comparisons of classification results and performance metrics (accuracy, precision, recall, F1-score) for all implemented algorithms.  
Each model file shows:
- Data preprocessing workflow
- Model configuration
- Training and prediction steps
- Evaluation results and visualizations

## Results

- **Best Performing Models:** Results are summarized within each notebook; generally, ensemble methods (Random Forest, Gradient Boosting, LightGBM, XGBoost) tend to outperform simpler baselines on this dataset.
- See individual notebooks for detailed performance metrics and confusion matrices.
