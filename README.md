# PCA From Scratch

A from-scratch derivation and Python implementation of **Principal Component Analysis** — built directly from the eigenvalues and eigenvectors of the data's covariance matrix, without `sklearn.decomposition.PCA`.

The accompanying mathematical derivation and code walkthrough are published in *Analytics Vidhya* (Medium publication, 77K+ followers).

## 📰 Companion articles

1. **[Derivation of Principal Component Analysis (PCA)](https://medium.com/analytics-vidhya/derivation-of-principal-component-analysis-pca-8453b0e782d7)** — full mathematical derivation from first principles: covariance matrix, the optimisation problem behind PCA, generalised Lagrangian, and the link to eigenvalue decomposition.
2. **[PCA from First Principles — Code Walkthrough](https://medium.com/analytics-vidhya/principal-component-analysis-from-first-principles-code-walkthrough-pca-b7cc471d7c63)** — implementation in plain NumPy, step by step, matching the mathematics from the first article.

## What's in this repo

- `PCA.ipynb` — the notebook implementation:
  - Column standardisation (zero-centre + unit variance)
  - Manual computation of the covariance matrix
  - Eigendecomposition with `numpy.linalg.eig`
  - Sorting components by eigenvalue magnitude
  - Projecting data into the top-k principal components
  - Numerical comparison against `sklearn.decomposition.PCA` for sanity-checking

## The PCA pipeline (summary of the derivation)

1. Lay out the data matrix `X` — rows are observations, columns are features
2. Standardise each column (zero mean, unit variance)
3. Compute the covariance matrix `S = (1/n) · Xᵀ X`
4. Compute eigenvalues and eigenvectors of `S`
5. Sort eigenvectors by descending eigenvalue
6. Project `X` onto the top-k eigenvectors → reduced representation

## Run

```bash
pip install numpy scikit-learn matplotlib jupyter
jupyter notebook PCA.ipynb
```

## Why from-scratch?

`sklearn.decomposition.PCA(n_components=k)` is ten lines of code. The point of this project was to make every step inside those ten lines explicit — what the covariance matrix is geometrically, why eigendecomposition appears in the solution, what eigenvalues mean as a measure of variance along each principal axis — and then verify the from-scratch result matches scikit-learn numerically.

## License

MIT
