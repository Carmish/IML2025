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


# Exam Questions and Summary Outline (Overview)

## [Q1 Exercises Week 2-3 (Vector & Matrices)](W02/01-poses.ipynb)

<details>
<summary><strong>(a) Inner products, vector operations, distance metrics and relation to ML</strong></summary>

- inner products
- vector operations
  - addition/subtraction/scaling
- distance metrics
  - Euclidean distance (square root of dot )
  - Example of use: similarity between poses
  - Alternative: cosine similarity (in week 11.04, comparing faces based on HoG features)

</details>

<details>
<summary><strong>(b) Matrices and their operations + course applications</strong></summary>

- matrix operations (see W03 0x)
  - addition
  - scalar multiplication (relation to scaling of vectors)
  - matrix multiplication (relation to linear transformations)
  - transpose (flips and relation to inner products)
  - inverse (undoing transformations)
  - determinant (area scaling and invertibility)
  - orthogonal (relation to orthonormal bases and rotations)
  - (for all above, also include relation to applications within the course)
- Bases and transformations (week 11.05)

</details>

<details>
<summary><strong>(c) Linear equations/solutions and relation to matrices</strong></summary>

- linear systems 
- solving linear systems using matrix methods (using matrix multiplication, determinant and inverse)
- relation to fitting models to data (finding weights that minimize error between predictions and actual labels)

</details>


## [Q2 Exercise Week 4 (Linear Transformations)](W04/01-linear_algebra.ipynb)

<details>
<summary><strong>(a) Linear transformations in 2D/3D + relation to affine/non-linear</strong></summary>

_[tutorial-link](../Tutorials/04-transformations.ipynb)_
- Linear transformations
- transformations in 2D and 3D spaces
- types of linear transformations
  - scaling, shearing, reflections, and rotations (and extensions to higher dimensional linear transformations) 
  - non-commutativity
- linear transformations vs non-linear transformations including affine
  - translations
  - homogeneous coordinates for affine transformations

</details>

<details>
<summary><strong>(b) Learning linear/non-linear models using matrix inverses + complexity vs data</strong></summary>

- learning models using matrix inverses
  - seperate inputs/labels
  - construct design matrix
  - compute weights using inverse (accounting for non-square matrices)
- Examples:
  - linear model (inClass3)
  - polynomial model (increased complexity) (02)

</details>

<details>
<summary><strong>(c) Affine transforms, homogeneous coordinates, composition</strong></summary>

- composition of linear transformations (mixing multiple transformations into one matrix)
  - associativity
  - non-commutativity
- affine transformations (last part of [tutorial](../Tutorials/04-transformations.ipynb))
  - affine transformations
  - homogeneous coordinates for translations

</details>


## [Q3 Exercise Week 5 (Projections and Least Squares)](W05/01-tutorial-qa.ipynb)

<details>
<summary><strong>(a) Least squares (minimization) and projections</strong></summary>

- projections
- linear least squares as projection
- geometric interpretation

</details>

<details>
<summary><strong>(b) Least squares for model fitting + interpretation across model types</strong></summary>

- process of model fitting
  - types of linear models (via design matrix / kernel)
    - lines
    - polynomials
    - affine functions
    - multivariate functions (e.g., x and y coordinates) (W05 02)
- Interpretation of results for various types of models 
  - regression metrics ((R)MSE) (W07 02)
  - classification metrics (accuracy, precision, recall, F1-score) (W11 01)

</details>

<details>
<summary><strong>(c) Learning affine (multivariate) functions + linear optimization</strong></summary>

- process of learning affine functions
  - design matrix for affine, multivariate functions (W05 02)
  - compute weights using least squares normal equation: $w = (A^T A)^{-1} A^T b$

</details>


## [Q4 Exercise Week 6 (Mandatory 1)](IML_Assignments/GazeEstimation/W06/01-data-preprocessing.ipynb)

<details>
<summary><strong>(a) Preprocessing and feature extraction (Mandatory 1)</strong></summary>

- Explain the gaze estimation in general
  - input/output
- Pupil center coordinate extraction using image thresholding and contour detection:
  - process frames (isolating eye region)
  - Threshold value
    - Thresholding the image to highlight potential pupil regions according to intensity (pupils=dark).
  - Edge Detection
    - Detect edges in the thresholded image using the Canny edge detector. 
  - Contour Detection
    - Find contours within the edge-detected image.
  - Ellipse Fitting
    - Fit ellipses to the detected contours that meet specific criteria (e.g., aspect ratio).
  - Pupil Center Detection
    - Identify the most likely pupil center based on ellipse fitting within a defined bounding box.

</details>

<details>
<summary><strong>(b) Model predictions and learning (Mandatory 1)</strong></summary>

- Explain the gaze estimation in general
- Model creation for gaze estimation:
  - Identify input/output and model parameters for the models (one for x, one for y, using same input features)
  - isolate unknown model parameters and knowns into design matrix
  - calibrate model parameters using training data (least squares solution for each dimension)
  - make predictions on test data using learned model parameters

</details>

<details>
<summary><strong>(c) Model evaluation (Mandatory 1)</strong></summary>

- Explain the gaze estimation in general
- Metrics for evaluation of model performance:
  - RMSE (Root Mean Square Error): The square root of the average of squared differences between predicted and actual gaze positions across both x and y coordinates.
  - MAE x and y: Mean Absolute Error for x and y coordinates separately, measuring average absolute differences.
  - Euclidean distance error: Average Euclidean distance between predicted and actual gaze positions.
- Impact of what pattern/subject is used for training vs testing 

</details>

<details>
<summary><strong>(d) Vector space, basis, independence + relation to ML (optional Week 12)</strong></summary>

- vector
- vector space
- basis
- linear independence
- relation to machine learning
  - data representation using vectors
    - each element of the vector represents a feature
    - each vector represents a data point
    - dataset represented as a matrix (rows=data points, columns=features)
  - Relevanse of basis and independence
    - basis vectors define the coordinate system for representing data
    - linear independence ensures that features provide unique information
  - Basis transformations (PCA)
    - changing the representation of data to a different basis, where new features arise as linear combinations of original features (PCA, to reduce dimensionality by combining correlated features)

</details>


## [Q5 Exercise Week 7 (Model Complexity, Model selection and noise)](W07/01-polynomial_regression.ipynb)

<details>
<summary><strong>(a) Least squares model fitting (design matrix, kernels, polynomials, affine, multivariate)</strong></summary>

- process of model fitting
  - types of linear models (via design matrix / kernel)
    - lines
    - polynomials
    - affine functions
    - multivariate functions (e.g., x and y coordinates) (W05 02)
- Interpretation of results for various types of models 
  - regression metrics ((R)MSE) (W07 02)
  - classification metrics (accuracy, precision, recall, F1-score) (W11 01)

</details>

<details>
<summary><strong>(b) Data quality, uncertainty, overfitting vs underfitting</strong></summary>

- overfitting/underfitting (W07 02) 
- data quality
  - uncertainty (aleatoric vs. epistemic)
  - noise variance and outliers (W09 02)
  - missing data (W09 03)
  - imbalanced data (W11 01)

</details>

<details>
<summary><strong>(c) Generalization + evaluation (splits, CV, metrics)</strong></summary>

- overfitting/underfitting (W07 02) 
- impact of noise variance and outliers (W09 02)
- imbalanced data (W11 01)
- Evaluation methods
  - train-test splits (W07 02)
  - cross-validation ([W07 tutorial 02](../Tutorials/07/02-cv_sklearn.ipynb))
  - performance metrics 
    - regression metrics ((R)MSE, R^2) (W07 02 Task 3-5)
    - classification metrics (accuracy, precision, recall, F1-score) (W11 01)

</details>


## [Q6 Exercise Week 8 (Filtering)](W08/01-data_cleaning.ipynb)

<details>
<summary><strong>General overview (tutorials + where in the week this appears)</strong></summary>

Overview of relevant material from the tutorials and exercises related to filtering in image processing and computer vision:
- [08 Tutorial](../Tutorials/08-filters.ipynb)
  - blur filter (gaussian and mean) for noise reduction
  - partial derivatives for edge detection using filters
  - convolving blur+edge-filter with image
- filtering gaze data (W08 01)
  - gaussian filter for smoothing noisy gaze data (Task 2-4)
  - partial derivatives filter for detecting saccades (Task 5-9)
  - identification of individual fixations using detected saccades (Task 10-13)
  - analyzing results (Task 14-15)
  - using combined signal (Task 17-18)
- filter basics (W08 02)
  - shifting pixels using filters (Task 1)
  - blurring using gaussian filter (Task 2)
  - template matching of sunflower (Task 3)
  - sharpening filter (Task 4)
  - sobel filters (Task 5)
  - convolution implementation (Task 6)
+ maybe some HOG features exercises from week 11?
  - HOG feature extraction and how to measure similarity (W11 03)
  - HOG for face detection (W11 04)

</details>

<details>
<summary><strong>(a) Filtering (1D/2D/n-D), convolution/correlation, smoothing, noise</strong></summary>

- Gaussian and mean filters for noise reduction (W08 Tutorial)
- Convolution for applying filters (W08 Tutorial)
- Correlation for template matching (W08 02 Task 3)
- Implementation of 2D convolution (W08 02 Task 6)
- Use case: W08 01
  - Gaussian filter for smoothing noisy gaze data (Task 2-4)
  - Partial derivatives filter for detecting saccades (Task 5-9)
  - Identification of individual fixations using detected saccades (Task 10-13)
  - Analyzing results of filtering (Task 14-15)
  - Using combined signal for improved filtering (Task 17-18)

</details>

<details>
<summary><strong>(b) Derivatives, gradients, edges + link to HOG</strong></summary>

- Partial derivatives for edge detection using filters (W08 Tutorial)
- saccade detection using partial derivatives filter (W08 01 Task 5-9)
- combined signal for improved saccade detection (W08 01 Task 17-18)
- HOG feature extraction and similarity measurement (W11 03)
- HOG for face detection (W11 04)

</details>


## [Q7 Exercise Week 9 (Understanding Data and Descriptive Methods)](W09/01-correlation-covariance-intro.ipynb)

<details>
<summary><strong>(a) Correlation & covariance: definition, calculation, interpretation, use</strong></summary>

- key characteristics of covariance and correlation (01 Task 1)
  - how they are calculated
  - purpose
  - how to interpret them
  - when to use which
- example and reflections (01 Task 2-4)

</details>

<details>
<summary><strong>(b) Descriptive stats for model selection & generalization</strong></summary>

- model fitting: mean fitted polynomial (02 Task 1-2)
  - variability of the fitted polynomials
  - impact of outliers and noise variance on model fitting
- generalizability (02 Task 3-4)
  - MSE of Test data vs Train data
- model complexity (02 Task 5)
  - MSE comparison - overfitting?
- covaariance/correllation of model parameters (02 Task 6)
  - overfitting/sinsitivity to data changes

</details>

<details>
<summary><strong>(c) Noise, outliers, missing data</strong></summary>

- impact of outliers and noise variance on model fitting (W09 02 Task 1-2)
- handling missing data (W09 03 Task 1-5)
  - zero filling (Task 1)
  - mean imputation (Task 2)
  - temporal interpolation (Task 3)
  - method comparison (Task 4-5)
    - zero filling -> shrinking (Task 6)
    - correlation preservation (Task 7)

</details>

<details>
<summary><strong>(d) Uncertainty/noise/data cleaning across ML tasks (Gaussian etc.)</strong></summary>

- uncertainty (aleatoric vs. epistemic)
- impact of outliers and noise variance in model fitting (W09 02 Task 1-2)
- data cleaning 
  - filtering gaze data (W08 01)
  - handling missing data (W09 03 Task 1-5)
  - imbalanced data (W11 01)

</details>


## [Q8 Exercise Week 10-11 (Classification)](W10/01-logistic_regression.ipynb)

<details>
<summary><strong>(a) Linear classification, kernels, boundaries</strong></summary>

- Linear classification learned with Least Squares (W10 02)
- Maximum Margin Classifier
- Support Vector Classification (SVC) for linear classification
- Non-linear classification using feature mapping (to polar coordinates) (W10 03)
- Support Vector Machine (SVM) with Kernel trick for non-linear classification

</details>

<details>
<summary><strong>(b) Logistic regression and classification boundaries</strong></summary>

- Classification
- Logistic Regression (W10 01)
- Sigmoid and decision boundary (log(odds) graph)
  - binary classification using logistic regression
  - logistic regression for evaluating which features are important for classification
- Linear classification learned with Least Squares (W10 02)
- Maximum Margin Classifier
- Support Vector Classification (SVC) for linear classification 
- Non-linear classification using feature mapping (to polar coordinates) (W10 03)
- Support Vector Machine (SVM) with Kernel trick for non-linear classification

</details>

<details>
<summary><strong>(c) Linear vs non-linear boundaries incl. SVM (+ optional HOG)</strong></summary>

- Linear classification learned with Least Squares (W10 02)
- Maximum Margin Classifier
- Support Vector Classification (SVC) for linear classification 
  - cross-validation to determine support vectors
- Non-linear classification using feature mapping (to polar coordinates) (W10 03)
- Support Vector Machine (SVM) with Kernel trick for non-linear classification
- HOG feature extraction and similarity measurement (W11 03)
- HOG for face detection (W11 04)

</details>


## [Q9 Exercise Week 11 (Evaluation)](W11/01-metrics.ipynb)

<details>
<summary><strong>(a) Metrics / evaluation of classifiers</strong></summary>

- confusion matrix (Task 3)
- Different metrics for classification evaluation (Task 5)
  - Accuracy
  - Precision
  - Recall
  - F1-score
  - Specificity (true negative rate)
  - MCC (Matthews correlation coefficient)
    - Formula:
      - $MCC=\frac{TP \cdot TN-FP \cdot FN}{\sqrt{(TP+FP)(TP+FN)(TN+FP)(TN+FN)}}$
    - Score range: -1 to +1
    - Interpretation: 
      - +1 -> perfect prediction, 
      - 0 -> random prediction, 
      - -1 -> total disagreement between prediction and observation
  - ROC curve and Precision-Recall curve
    - AUC (Area Under the Curve) for ROC and Precision-Recall curves
    - Optimal threshold based on ROC curve

</details>

<details>
<summary><strong>(b) Metrics / evaluation of regression</strong></summary>

- MAE (Mean Absolute Error)
- SSD (Sum of Squared Differences)
- MSE (Mean Squared Error)
- RMSE (Root Mean Squared Error)
- Regression metrics for evaluation of gaze estimation model performance (W06 02) 
  - RMSE on both x and y coordinates
  - MAE for x and y coordinates separately
  - Euclidean distance error: Average Euclidean distance between predicted and actual gaze positions.
- Evaluation of Neural Networks (W14 01)
  - Training and validation loss curves (Overfitting and underfitting detection)
  - Absolute error for x and y coordinates
  - MSE for model performance comparison

</details>

<details>
<summary><strong>(c) Imbalanced data for classification and regression</strong></summary>

- Class imbalance problem 
  - classification
  - regression
- Techniques to handle imbalanced data in classification
  - Oversampling
  - Undersampling
  - Data augmentation
  - selection of suitable evaluation metrics (and ROC curve vs precision-recall curve)
- Techniques to handle imbalanced data in regression
  - missing data (W09 03)

</details>


## [Q10 Exercise Week 12 + Assignment 2 (Principal Component Analysis)](IML_Assignments/W12/01-pca_intro.ipynb)

<details>
<summary><strong>(a) Basis and transformations</strong></summary>

- transformations [W04 Tutorial](../../Tutorials/04-transformations.ipynb)
  - linear transformations
  - affine transformations
- basis
  - what is a basis
  - change of basis [W11 05](../../W11/05-basis.ipynb)
  - eigenbasis
  - PCA as change of basis to eigenbasis of covariance matrix
  - normal distribution in eigenbasis (uncorrelated dimensions)

</details>

<details>
<summary><strong>(b) Dimensionality reduction and PCA (Mandatory 2 focus)</strong></summary>

- dimentionality reduction
- principal component analysis (PCA)
  - purpose
  - eigenvectors and eigenvalues
  - principal components (see plot in W12 01 task 1)
  - latent space
  - reconstruction error (see plot in W12 01 task 7)
- Example: PCA for face shape generation (W12 02)

</details>

<details>
<summary><strong>(c) Generating models and PCA</strong></summary>

- principal component analysis (PCA)
- PCA for face shape generation (W12 02)
  - interpolation in latent space (W12 02 Task 7)
    - linearity in latent vs data space
  - normal distribution (W12 02 Part 2 (Task 4->))

</details>

<details>
<summary><strong>(d) Eigenvalues, covariance matrix and basis</strong></summary>

- mean
- variance
- covariance matrix
- eigenvectors and eigenvalues
- basis
  - what is a basis
  - change of basis
  - eigenbasis
  - covariance matrix in eigenbasis (diagonal)
  - PCA as change of basis to eigenbasis of covariance matrix
  - normal distribution in eigenbasis (uncorrelated dimensions)

</details>


## [Q11 Exercise Week 13 (Clustering)](W13/01-Clustering.ipynb)

<details>
<summary><strong>(a) K-means and Mean shift</strong></summary>

- What is clustering and what is its purpose? (benefits and posible pitfalls) (Task 1)
- Explain the K-means clustering algorithm. (Task 3-7)
  - Converges to local minimum of whitin-cluster squared error (variance)
  - depends on the choice of k, sensitive to initial centers, sensitive to outliers
- Explain the Mean shift clustering algorithm. (Task 9-11)
  - Converges to modes of the data density (Formulates clustering as histogram partitioning)
  - does not require specifying number of clusters, can find arbitrarily shaped clusters
  - depends on choice of bandwidth parameter, computationally expensive for large datasets
- Compare K-means and Mean shift clustering algorithms. (Task 17)

</details>

<details>
<summary><strong>(b) K-means and Agglomerative clustering</strong></summary>

- What is clustering and what is its purpose? (benefits and posible pitfalls) (Task 1)
- Explain the K-means clustering algorithm. (Task 3-7)
  - Converges to local minimum of whitin-cluster squared error (variance)
  - depends on the choice of k, sensitive to initial centers, sensitive to outliers
- Explain the Agglomerative clustering algorithm. (Task 12-16)
  - Builds hierarchy of clusters by iteratively merging closest pairs of clusters
  - Does not require specifying number of clusters upfront, can capture complex cluster shapes
  - long runtime, choise of number of clusters or threshold
- Compare K-means and Agglomerative clustering algorithms. (Task 17)

</details>

<details>
<summary><strong>(c) K-means and ELBOW</strong></summary>

- What is clustering and what is its purpose? (benefits and posible pitfalls) (Task 1)
- Explain the K-means clustering algorithm. (Task 3-7)
  - Converges to local minimum of whitin-cluster squared error (variance)
  - depends on the choice of k, sensitive to initial centers, sensitive to outliers
- Explain the ELBOW method for selecting the number of clusters in K-means. (Task 8)
- What is the effect of choosing too few or too many clusters on the clustering results. (Task 8)

</details>


## [Q12 Exercise Week 14 (Neural networks)](W14/01-nn-gaze.ipynb)

<details>
<summary><strong>General overview (what a neural network is + forward/backprop)</strong></summary>

What is neural network:
- Composed of node layes
  - composed of different layers: input, hidden, output
  - each layer composed of neurons (nodes)
  - neurons connected with weights
  - resembling the human brain structure
- use a linear regression model
  - the weights on the edges between the nodes determines how much influence a node has on another node (and thus on the final output)
  - So, each node is composed of input data, weights, a bias or a threshold, and an output function (activation function)
- Data is passed between nodes feed forward
  Example:
  - y_hat: the predicted outcome for the problem:
    Should we go surfing or not? 
  - Features:
    - x1: 1 (is the wawes good? Yes!)
    - x2: 0 (is the beach crowd free? Unfortunatelly, no.)
    - x3: 1 (is the water sharkfree? Yes!)
  - weights:
    - w1: 5 (the weight for x1, it is very important to have good waves)
    - w2: 2 (the weight for x2, it is not so important if the beach is crowded)
    - w3: 4 (the weight for x3, it is pretty important to have sharkfree water)
  - threshold/bias:
    - b: -3 (we need a minimum score of 3 to go surfing, otherwise it is not worth it)
  - Prediction:
    - y_hat = x1*w1 + x2*w2 + x3*w3 + b = 1*5 + 0*2 + 1*4 - 3 = 6 > 0 -> go surfing!
- Rely on training data 
  - Cost Function: measures how well the neural network is performing
  - goal is to minimize the cost function by adjusting the weights and biases
  - gradient decent is used to determine which direction to adjust the weights and biases to minimize the cost function
- Neural Networks have multiple types (beyond the feed forward NN described above)
  - Convolutional Neural Networks (CNNs): used for e.g. image recognition
  - Recurrent Neural Networks (RNNs): used for sequential data like time series to predict next values

- Forward propagation:
  - input data is passed through the network layer by layer
  - each neuron applies weights, bias, and activation function to compute its output
  - final output is produced (prediction)
- Backpropagation: for training the network
  - output error is computed (loss function) as the difference between predicted output and actual target
  - error is propagated backwards through the network, measuring how much each weight contributed to the error using the chain rule
  - weights and biases are updated to minimize the error for the subsequent forward pass
  - this process is repeated iteratively until the network converges to a satisfactory level of performance
  - Optimization algorithm: Gradient Descent
    - used to minimize the loss function by iteratively adjusting the weights and biases
    - computes the gradient (partial derivatives) of the loss function with respect to each weight and bias
    - updates the weights and biases in the opposite direction of the gradient to reduce the loss
    - learning rate determines the step size for each update
  - different types of NN architectures and their applications:
    - static: e.g. OCR (image classification), SPAM detection (text classification)
    - recurrent NN: time series prediction, language modeling
    - Difference for the backpropagation:
      - static NN: backpropagation through layers
      - RNN: backpropagation through time (BPTT), considering temporal dependencies

</details>

<details>
<summary><strong>(a) Neural networks prediction (regression vs classification)</strong></summary>

- NN
- Forward propagation:
  - input data is passed through the network layer by layer
  - each neuron applies weights, bias, and activation function to compute its output
  - final output is produced (prediction)
- Backpropagation: for training the network
  - output error is computed (loss function) as the difference between predicted output and actual target
  - error is propagated backwards through the network, measuring how much each weight contributed to the error using the chain rule
  - weights and biases are updated to minimize the error for the subsequent forward pass
    - Optimization algorithm: Gradient Descent
  - this process is repeated iteratively until the network converges to a satisfactory level of performance

- CNN (Convolutional Neural Network) for classification:
  - input image is passed through convolutional layers to extract features
  - each convolutional layer applies filters to the input image to detect patterns (edges, textures, shapes)
  - features are flattened and passed through fully connected layers
  - final output layer produces class probabilities using some activation function (sigmoid for binary classification)
  - predicted class is determined by selecting the class with the highest probability
- Regression example: gaze estimation
  - input: coordinates of pupil
  - output: coordinates of gaze point on screen
  - loss function: Mean Squared Error (MSE) to measure the difference between predicted and actual gaze points
  - Learning: 
    - first model is trained with Least Squares and no hidden layers
    - then a NN with hidden layers is trained to try to improve performance
    - evaluation: compare MSE of both models on validation/test set to see if NN improves performance

</details>

<details>
<summary><strong>(b) Neural networks training (Gradients, chain rule, back/forward propagation)</strong></summary>

- NN
- Forward propagation:
  - input data is passed through the network layer by layer
  - each neuron applies weights, bias, and activation function to compute its output
  - final output is produced (prediction)
- Backpropagation: for training the network
  - output error is computed (loss function) as the difference between predicted output and actual target
  - error is propagated backwards through the network, measuring how much each weight contributed to the error using the chain rule
  - weights and biases are updated to minimize the error for the subsequent forward pass
  - this process is repeated iteratively until the network converges to a satisfactory level of performance
  - Optimization algorithm: Gradient Descent
    - used to minimize the loss function by iteratively adjusting the weights and biases
    - computes the gradient (partial derivatives) of the loss function with respect to each weight and bias
      - uses the chain rule to efficiently compute gradients for each layer
    - updates the weights and biases in the opposite direction of the gradient to reduce the loss
    - learning rate determines the step size for each update

</details>

<details>
<summary><strong>(c) Training and evaluation incl. over/underfitting</strong></summary>

- NN
- Forward propagation:
  - input data is passed through the network layer by layer
  - each neuron applies weights, bias, and activation function to compute its output
  - final output is produced (prediction)
- Backpropagation: for training the network
  - output error is computed (loss function) as the difference between predicted output and actual target
  - error is propagated backwards through the network, measuring how much each weight contributed to the error using the chain rule
  - weights and biases are updated to minimize the error for the subsequent forward pass
  - this process is repeated iteratively until the network converges to a satisfactory level of performance
  - Optimization algorithm: Gradient Descent
    - used to minimize the loss function by iteratively adjusting the weights and biases
    - computes the gradient (partial derivatives) of the loss function with respect to each weight and bias
    - updates the weights and biases in the opposite direction of the gradient to reduce the loss
    - learning rate determines the step size for each update
- Overfitting and underfitting:
  - Overfitting: model learns the training data too well, including noise and outliers
    - performs well on training data but poorly on unseen data
    - symptoms: low training error, high validation/test error 
  - Underfitting: 
    - model is too simple to capture the underlying patterns in the data
    - performs poorly on both training and unseen data
    - symptoms: high training error, high validation/test error

</details>

<details>
<summary><strong>(d) Architectures: fully connected / MLP vs CNN</strong></summary>

- Fully connected NN 
  - each neuron in one layer is connected to every neuron in the next layer
- Multi Layer Perceptron (MLP)
  - a type of fully connected NN with one or more hidden layers between input and output layers
  - Learning:
    - Predict an output based on input data by passing it through the network (forward propagation)
    - Adjust weights and biases based on the error between predicted and actual output (backpropagation)
    - Repeat (epochs) until the model converges to a satisfactory level of performance
- Convolutional Neural Network (CNN)
  - A specialized type of NN designed for processing grid-like data such as images (e.g. to perform image classification)
  - These are not necessarily fully connected! Instead, they use convolutional layers to extract features from the input data
  - Learning:
    - Input image is passed through convolutional layers to extract features
    - Features are flattened and passed through fully connected layers
    - Final output layer produces class probabilities using some activation function (sigmoid for binary classification)
    - Predicted class is determined by selecting the class with the highest probability

</details>

<details>
<summary><strong>(e) Loss functions, model complexity, cross-validation</strong></summary>

- NN
- Loss functions:
  - measure how well the neural network is performing
  - common loss functions:
    - Mean Squared Error (MSE) for regression tasks (Task 11)
      - measures the average squared difference between predicted and actual values
    - Cross-Entropy Loss for classification tasks
      - measures the difference between predicted class probabilities and actual class labels
- Model complexity:
  - refers to the capacity of the neural network to learn complex patterns in the data
  - influenced by factors such as:
    - number of layers
    - number of neurons per layer
    - choice of activation functions (non-linear functions allow the network to learn more complex patterns)
  - The performance of the model is also affected by hyperparameters such as: epochs and learning rate
  - trade-off between underfitting and overfitting
- Cross-validation: to evaluate generalization performance 

</details>
