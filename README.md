# IML 2025

## Weekly overview

| Week | Topics | main themes |
|---:|---|---|
| [W00](./W00) |Setup| Python basics (environment setup, intro exercise, working with scripts/notebooks) |
| [W01](./W01) |Intro to ML, data and vectors| Practical intro to **Python & NumPy**: vectors, dot products, slicing, broadcasting, basic linear algebra with arrays |
| [W02](./W02) |Linear algebra, Matrices and their solutions| **Vector distance metrics** via pose comparison (“Evaluating poses”) + **data collection** workflow (eye image dataset; prerequisite for Mandatory Assignment 1) |
| [W03](./W03) |Inverse and Transformations| **Matrix inverse & solving linear systems** + **2D/3D transformations** (rotation/translation) as linear maps |
| [W04](./W04) |Least Squares and overdetermined systems| **Least squares** intuition + **polynomials** + **line fitting** + applying **transformations** to data/coordinates |
| [W05](./W05) |Projections and Least Squares| **Projections / orthogonality** + **least squares as projection** + **affine spatial regression** (mapping between coordinate systems) |
| [W06](./GazeEstimation/W06) |Mandatory 1: GazeEstimation| **End-to-end gaze estimation pipeline** (eye/face detection + normalization) + **regression from image/features to gaze point/vector** + **calibration & evaluation** (error metrics) + **temporal smoothing / robustness** for real-time use |
| [W07](./W07) |Model Complexity, Model selection and noise| **Polynomial regression** + **bias/variance & overfitting** + **model selection** (validation) + effects of **noise** |
| [W08](./W08) |Filtering| **Data cleaning** + **filter basics** (moving average / low-pass intuition) + smoothing noisy signals over time |
| [W09](./W09) |Understanding Data and Descriptive Methods| **Descriptive statistics** + **correlation & covariance** + **model fitting diagnostics** + handling **missing data** |
| [W10](./W10) |Classification| **Logistic regression** + **decision boundaries** (linear vs nonlinear features) + probability interpretation |
| [W11](./W11) |Classification II and Evaluation| **Evaluation metrics** (precision/recall/F1) + **confusion matrix** + feature representations (**HOG features**) + **HOG classifier** |
| [W12](./W12) |Mandatory 2: Principal Component Analysis (PCA)| **PCA** (dimensionality reduction) + interpreting components + **PCA-based shape generation** / reconstruction |
| [W13](./W13) |Clustering| **Unsupervised learning** + clustering objectives (k-means intuition) + cluster evaluation/interpretation |
| [W14](./W14) |Neural Networks| **Neural networks for gaze** (MLP/CNN intuition) + **optimization** (gradient descent/backprop basics) + practical training considerations |



# Exam Questions

## [Q1 Exercises Week 2-3 (Vector & Matrices)](W02/01-poses.ipynb)

### (a) Focus on inner products, vector operations, distance metrics and their relation to ML (evaluation and other metrics). You may relate this to week 10 (evaluation) but focus on vectors.

### (b) Focus on matrices and their operations (addition, multiplication, transpose, inverse, determinant, orthogonal). Relate them to their application within the course (e.g., transformations, basis in week 11).

### (c) Focus on how linear equations and their solutions are related to matrices.

## [Q2 Exercise Week 4 (Linear Transformations)](W04/01-linear_algebra.ipynb)

### (a) Use the tutorial to focus on exploring linear transformations in 2D and 3D spaces, including operations such as scaling, shearing, reflections, rotations, and translations, while drawing connections to their extensions in higher-dimensional linear transformations. Additionally, you should explain the relationship between linear transformations and non-linear transformations including affine, thus bridging the gap between linear and more complex transformations.

### (b) Focus on how linear and non-linear models can be learned using matrix inverses. Discuss the relationship between model complexity (e.g., polynomial degree) and the amount of data needed to accurtely train these models with matrix inverses.

### (c) Focus on affine transformations, homogeneous coordinates and composition of linear transformations.

## [Q3 Exercise Week 5 (Projections and Least Squares)](W05/01-tutorial-qa.ipynb)

### (a) Focus on the relation between linear least squares (function minimization) and projections.

### (b) Focus on linear least squares problems for model fitting (design matrix, kernel, lines, polynomials, affine, and other multivariate functions) and the interpretation of results for various types of models (see week 7).

### (c) Learning of Affine (multivariate) functions and linear optimization.

## [Q4 Exercise Week 6 (Mandatory 1)](IML_Assignments/GazeEstimation/W06/01-data-preprocessing.ipynb)

### (a) Focus on preprocessing and feature extraction in Mandatory 1

### (b) Focus on model predictions and learning Mandatory 1

### (c) Focus on model evaluation in Mandatory 1

### (d) Describe vector space, basis, independence and how these are related to concepts in machine learning (learning, transformations etc). You MAY include exercises week 12 if you have done them.

## [Q5 Exercise Week 7 (Model Complexity, Model selection and noise)](W07/01-polynomial_regression.ipynb)

### (a) Linear least squares problems for model fitting (design matrix, kernel, lines, polynomials, affine, and other multivariate functions).

### (b) Discuss the relationship between data quality, uncertainty, and the challenges of overfitting and underfitting in model learning.

### (c) Discuss how factors affect a model’s ability to generalize to unseen data. Relate this to concepts of data evaluation, such as train-test splits, cross-validation, and performance metrics, to assess a model’s predictive capability and robustness.

## [Q6 Exercise Week 8 (Filtering)](W08/01-data_cleaning.ipynb)

### (a) Focus on filtering (1D, 2D, and n-D convolution and correlation, blurring and smoothing, and noise).

### (b) Focus on filtering for derivatives, gradients, and edges. You may include how these operations can be used to construct features such as HOG.

## [Q7 Exercise Week 9 (Understanding Data and Descriptive Methods)](W09/01-correlation-covariance-intro.ipynb)

### (a) Describe correlation and covariance, explain how they are calculated, and discuss how they are useful for understanding data and for descriptive analysis.

### (b) Explain how descriptive statistics can be used to assess model selection and the generalization ability of machine learning models.

### (c) Describe noise, outliers, and missing data.

### (d) Focus on uncertainty, noise, data cleaning in relation to regression, classification, clustering or dimensionality reduction (Covariance, distributions (e.g Normal/Gaussian))

## [Q8 Exercise Week 10-11 (Classification)](W10/01-logistic_regression.ipynb)

### (a) Linear classification, kernels, and classification boundaries

### (b) Logistic regression and classification boundaries

### (c) Linear and non-linear decision boundaries including SVM (include week 10) and possibly HOG features.

## [Q9 Exercise Week 11 (Evaluation)](W11/01-metrics.ipynb)

### (a) Metrics/Evaluation of Classifiers

### (b) Metrics/Evaluation of Regression (Since there is no you may use assignment 1 and week 13/14 as part of your sescription)

### (c) Imbalanced data for classification and regression

## [Q10 Exercise Week 12 + Assignment 2 (Principal Component Analysis)](IML_Assignments/W12/01-pca_intro.ipynb)

### (a) Basis and transformations

### (b) Dimensionality reduction and PCA. Focus on mandatory 2

### (c) Generating models and PCA

### (d) Eigenvalues, covariance matrix and basis

## [Q11 Exercise Week 13 (Clustering )](W13/01-Clustering.ipynb)

### (a) K-means and Mean shift

### (b) K-means and Algomerative clustering

### (c) Kmeans and ELBOW

## [Q12 Exercise Week 14 (Neural networks)](W14/01-nn-gaze.ipynb)

### (a) Neural networks prediction (regression vs classification)

### (b) Neural networks training (Gradients, the chain rule and back/forward propagation)

### (c) Training and Evaluation including over/underfitting

### (d) Model architectures: Difference between fully connected /multi layer perceptron (MLP) and CNN

### (e) Loss functions, model complexity, cross-validation.
