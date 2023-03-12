
### NumPy
Library for numerical computing

Provides data structures, algorithms, and glue needed for most scientific and numerical applications, including:
- Multidimensional array object *[[BEFORE/OldOrg/40 - Knowledge Base/41 - Computing/21 - Data Science and AI/ndarray]]*
- Functions for element-wise computations with arrays or mathematical operations between arrays
- Tools for reading and writing array-based datasets to/from disk
- Linear algebra operations, Fourier transform, and random number generation
- C API to enable Python extensions, C, and C++ code to access NumPy data structures

### Pandas
Library to work with tabular data. Allows reshaping, aggregating, slicing and dicing, and producing subsets of data.

Primary objects are:
- DataFrame - tabular, column-oriented data structure with row and column labels
- Series - one-dimensional labeled array

### matplotlib
Library for producing plots and other 2D data visualizations.

### Jupyter Notebook / iPython
The Jupyter Project is an Open-source project of which Jupyter Notebook is the best-known component.
Interactive notebook that allows Python, Markdown, and HTML blocks to produce a document.

### SciPy
Collection of Python packages dealing with a number of foundational problems in scientific computing.
- **scipy.integrate**: Numerical integration routines and differential equation solvers
- **scipy.linalg**: Linear algebra routines and matrix decompositions beyond what is available from *[[numpy]].linalg*
- **scipy.optimize**: Function optimizers (minimizers) and root-finding algorithms
- **scipy.signal**: Signal processing tools
- **scipy.sparse**: Sparse matrices and sparse linear system solvers
- **scipy.special**: Wrapper around SPECFUN, a FORTRAN library implementing many common mathematical functions, such as the `gamma` function
- **scipy.stats**: Standard continuous and discrete probability distributions (density functions, samplers, continuous distribution functions), various statistical tests, and more descriptive statistics

### Scikit-Learn
General purpose machine learning toolkit.
- **Classification**: SVM, nearest neighbors, random forest, logistic regression, etc.
- **Regression**: Lasso, ridge regression, etc.
- **Clustering**: _k_-means, spectral clustering, etc.
- **Dimensionality reduction**: PCA, feature selection, matrix factorization, etc.
- **Model selection**: Grid search, cross-validation, metrics
- **Preprocessing**: Feature extraction, normalization

### statsmodels
Statistical analysis package. Algorithms for classical statistics and econometrics.
-   **Regression models**: linear regression, generalized linear models, robust linear models, linear mixed effects models, etc.
-   Analysis of variance (ANOVA)
-   **Time series analysis**: AR, ARMA, ARIMA, VAR, and other models
-   **Nonparametric methods**: Kernel density estimation, kernel regression
-   Visualization of statistical model results

## Standard Imports
```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
import statsmodels as sm
```

---
# Source
[[Python for Data Analysis]]




