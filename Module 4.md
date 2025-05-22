# Module 4: Model Performance and Advanced Regression Techniques

## Question 1: Model Performance and Measurement

### Definition
- Model performance refers to how effectively a model predicts numeric outcomes
- Measured by evaluating accuracy through various metrics
- Visualizations, especially residual plots, are crucial for understanding model suitability

### Performance Computation
- Compare observed vs. predicted outcomes
- Store outcomes in vectors for computation
- Calculate residuals: observed - predicted
- Summarize residuals using statistical functions

### Key Performance Metrics

#### 1. Sum-of-squared errors (SSE)
- Objective function minimized by OLS regression
- Formula: SSE = ∑ (yi − ŷi)²
- Minimizing SSE finds least biased parameter estimates

#### 2. Mean Squared Error (MSE)
- Components:
  - Irreducible variation
  - Model bias
  - Model variance
- Used in methods like ridge regression

#### 3. Root Mean Squared Error (RMSE)
- Primary measure of model performance
- Estimated using resampling techniques
- Lower values indicate better performance

#### 4. R-squared (R²)
- Proportion of variance explained by model
- Higher values indicate better fit
- Used alongside RMSE for performance assessment

### Evaluation Methods
- Resampling techniques (e.g., cross-validation)
- Diagnostic plots:
  - Residuals vs. predicted values
  - Observed vs. predicted values

## Question 2: Bias and Variance Impact on Model Performance

### Components of Model Performance
- Mean Squared Error (MSE) can be divided into:
  - Model bias
  - Model variance

### Bias
- Error from approximating complex problems with simpler models
- High bias indicates under-fitting
- Linear regression minimizes bias component

### Variance
- Amount model prediction changes with different training data
- High variance indicates over-fitting
- Affected by:
  - Model complexity
  - Correlated predictors
  - Data stability

### Bias-Variance Trade-off
- Linear regression: Minimizes bias
- Regularization methods:
  - Ridge regression
  - Lasso
  - Elastic net
- Complex models:
  - Lower potential bias
  - Higher potential variance
- Regularization techniques combat over-fitting

## Question 3: Performance Computation in R

### Manual Calculation
```r
# Calculate residuals
residuals <- observed - predicted

# Summarize residuals
summary(residuals)
```

### Using caret Package
```r
# Load package
library(caret)

# Set seed for reproducibility
set.seed(100)

# Train model
model <- train(
  x = solTrainXtrans,
  y = solTrainY,
  method = "lm",
  trControl = ctrl
)

# View results
print(model)
```

### Diagnostic Plots
- Residuals vs. predicted values
- Observed vs. predicted values

## Question 4: Linear Regression Assumptions

### 1. Linearity
- **Assumption**: Relationship falls along hyperplane
- **Importance**: Model structure assumes linear combination
- **Problems if Violated**:
  - Sub-optimal performance
  - Curvature in residual plots
  - Need for manual feature engineering

### 2. Independence/Collinearity
- **Assumptions**:
  1. No perfect collinearity
  2. Samples > predictors
- **Importance**: Ensures unique parameter estimates
- **Problems if Violated**:
  - Non-unique coefficients
  - Unstable estimates
  - Increased standard errors
  - Unstable predictions

### 3. Outliers/Influential Observations
- **Impact**: Large residuals have exponential effect
- **Problems**:
  - Parameter estimate distortion
  - Regression line deviation
- **Solutions**:
  - Robust regression
  - Alternative metrics
  - Support Vector Machines

### 4. Residual Distribution
- **Assumption**: Minimal distribution assumptions
- **Importance**: Random scatter about zero
- **Problems if Violated**:
  - Non-linear patterns
  - Unequal variance
  - Inadequate model structure

## Question 5: Comparison of Regression Methods

### Comparison Table
| Feature | Ridge Regression | Lasso Regression | Elastic Net |
|---------|-----------------|------------------|-------------|
| Model Type | Penalized Linear | Penalized Linear | Penalized Linear |
| Objective | Minimize SSE + penalty | Minimize SSE + penalty | Minimize SSE + penalties |
| Bias-Variance | Increase bias, reduce variance | Increase bias, reduce variance | Increase bias, reduce variance |
| Collinearity | Shrinks correlated coefficients | Picks one, ignores others | Combination approach |
| Coefficient Shrinkage | Towards zero, not zero | Towards zero, can be zero | Combination approach |
| Feature Selection | No explicit selection | Explicit selection | Combination approach |
| Penalty Term | L2 penalty | L1 penalty | L1 + L2 penalties |

### Use Cases

#### Ridge Regression
- Many correlated predictors
- All predictors potentially relevant
- Example: Solubility data with collinear predictors

#### Lasso Regression
- Feature selection needed
- Many irrelevant predictors
- Predictors > observations
- Example: Solubility data with feature selection

#### Elastic Net
- Combines benefits of both
- Not detailed in source material

## Question 6: Box-Cox Transformations in Solubility Case Study

### Application Purpose
- Remove skewness from continuous predictors
- Improve model performance

### Alternative Techniques
- Not detailed in source material

### Skewness Impact
- Not detailed in source material

## Question 7: Multicollinearity in Linear Regression

### Effects on Coefficients
- Non-unique regression coefficients
- Loss of meaningful interpretation
- Unstable parameter estimates
- Large coefficient magnitudes
- Increased standard errors
- Unstable predictions

### Addressing Methods

#### 1. Predictor Removal
- Remove collinear predictors
- Example: Remove predictors with correlations > 0.9
- Limitations:
  - May not eliminate all collinearity
  - Reduces predictor count

#### 2. Parameter Shrinkage
- Ridge regression
- Lasso
- Elastic net
- Benefits:
  - More stable coefficients
  - Better predictive performance

### Additional Methods
- PCA pre-processing
- Partial Least Squares (PLS)

## Question 8: Advanced Regression Methods

### 1. Neural Networks
- **Description**: Nonlinear regression models
- **Structure**: f(x) = γ0 + ∑ hk
- **Parameters**: H(P + 1) + H + 1
- **Training**: Back-propagation
- **Over-fitting Prevention**:
  - Early stopping
  - Weight decay
- **Tuning**: Weight decay (λ), hidden units

### 2. MARS
- **Description**: Piecewise linear model
- **Features**: Hinge functions
- **Training**: Iterative search
- **Advantages**:
  - Interpretable
  - Minimal preprocessing
  - Handles various predictors

### 3. SVM for Regression
- **Description**: Kernel-based model
- **Features**:
  - Robust to outliers
  - ε-insensitive tube
  - Support vectors
- **Tuning**: Cost value, kernel parameters

### 4. KNN for Regression
- **Description**: Distance-based prediction
- **Process**: K nearest neighbors
- **Preprocessing**: Centering and scaling
- **Tuning**: Number of neighbors (K)

## Question 9: Tree-Based Methods

### 1. Basic Regression Trees
- **Description**: Partition data into homogeneous groups
- **Prediction**: Constant values in terminal nodes
- **Training**: CART algorithm
- **Advantages**:
  - Interpretable
  - Handles various predictors
  - Implicit feature selection
- **Disadvantages**:
  - Sub-optimal performance
  - Instability
  - Limited predictions

### 2. Regression Model Trees
- **Description**: Linear models in terminal nodes
- **Training**: Similar to basic trees
- **Advantages**:
  - Better extreme predictions
  - Maintains interpretability
- **Challenges**: Collinearity in nodes

### 3. Rule-Based Models
- **Description**: If-then rules with predictions
- **Features**:
  - Highly interpretable
  - Handles various predictors
  - Models sub-populations
- **Structure**: Conditions and linear models

### 4. Bagged Trees
- **Description**: Bootstrap aggregating
- **Process**:
  1. Select number of models
  2. Generate bootstrap samples
  3. Train unpruned trees
  4. Average predictions
- **Benefits**:
  - Reduces variance
  - Improves stability
  - Better performance
- **Tuning**: Number of trees 