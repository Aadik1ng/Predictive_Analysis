# Module 5: Classification Models and Evaluation

## Question 1: Probability Calibration and Methods

### Importance of Probability Calibration
- Classification models generate continuous-valued predictions (probabilities)
- Some models (neural networks, PLS) need transformation (softmax) for probability-like values
- Models also generate discrete predicted classes for practical decisions
- Evaluation differs from regression (RMSE, R² not appropriate)
- Calibration plots assess probability quality

### Calibration Plot Process
1. Score samples with known outcomes (test set)
2. Bin samples by class probabilities (e.g., [0, 10%], (10%, 20%], etc.)
3. Calculate observed event rate for each bin
4. Plot bin midpoint vs. observed rate
5. 45° line indicates well-calibrated probabilities

### Calibration Methods

#### 1. Platt Scaling
- Uses sigmoidal transformation
- Estimates parameters (β₀, β₁)
- Improves calibration of model predictions
- Example: Improved QDA model calibration

#### 2. Bayesian Methods
- Uses Bayes' Rule for recalibration
- Post-processes probabilities using training set
- Improves calibration of model predictions
- Note: Class probabilities from Bayes' Rule may need recalibration

## Question 2: Confusion Matrix and Metrics

### Confusion Matrix Structure
|             | Predicted Event | Predicted Nonevent |
| :---------- | :-------------- | :----------------- |
| Observed Event   | TP (True Positive)  | FN (False Negative)    |
| Observed Nonevent| FP (False Positive) | TN (True Negative)     |

### Key Metrics

#### 1. Overall Accuracy
- Formula: (TP + TN) / Total Samples
- Example: 154/200 = 77% for credit data
- Compare to no-information rate (benchmark)

#### 2. Kappa Statistic
- Measures agreement beyond chance
- Formula: (O - E) / (1 - E)
- Range: -1 to 1
- Values 0.30-0.50 indicate reasonable agreement

#### 3. Sensitivity (True Positive Rate)
- Formula: TP / (TP + FN)
- Measures correct positive predictions
- Example: 40% for bad credit prediction

#### 4. Specificity (True Negative Rate)
- Formula: TN / (TN + FP)
- Measures correct negative predictions
- Example: 92.9% for bad credit prediction

## Question 3: Profit-Based Metrics and Error Costs

### Commercial Applications
- Goals beyond accuracy:
  - Maximize investment return
  - Improve customer satisfaction
  - Lower inventory costs
  - Reduce fraud costs

### Cost Matrix Example
|             | Response | Nonresponse |
| :---------- | :------- | :---------- |
| Response   | $26.40   | −$2.00      |
| Nonresponse| −$28.40  | –           |

### Cost Metrics

#### 1. Proportion of Costs (PCF)
- Formula: (P × C(+|−)) / (P × C(−|+) + (1 − P) × C(+|−))
- Where:
  - P: Prior probability
  - C(−|+): False Negative cost
  - C(+|−): False Positive cost

#### 2. Normalized Expected Cost (NEC)
- Formula: PCF × (1 − TP) + (1 − PCF) × FP
- Scales total cost between 0 and 1
- Considers:
  - Event prevalence
  - Model performance
  - Error costs

## Question 4: ROC Curves and Lift Charts

### ROC Curves
- Purpose: Determine effective probability thresholds
- X-axis: 1 - Specificity (False Positive Rate)
- Y-axis: Sensitivity (True Positive Rate)
- Perfect model: Step function (AUC = 1)
- Random model: 45° diagonal (AUC ≈ 0.50)
- AUC: Single metric for model comparison

### Lift Charts
- Purpose: Assess event detection ability
- Process:
  1. Rank samples by probability
  2. Calculate cumulative event rate
  3. Compare to random selection
- Perfect model: All events in top M samples
- Random model: 45° diagonal
- Lift: Improvement over random selection

### Comparison
- ROC: Trade-off between sensitivity/specificity
- Lift: Event concentration in top predictions
- Both use class probabilities differently
- AUC: Overall performance metric
- Lift: Efficiency gain over random targeting

## Question 5: Concrete Strength Prediction

*Note: This question is not addressed in the source materials.*

## Question 6: RMSE, MAE, and R² in Model Validation

*Note: These metrics are mentioned as not appropriate for classification, but not detailed in the source materials.*

## Question 7: Comparison of Classification Methods

### Comparison Table
| Feature | LDA | Logistic Regression | PLS-DA |
|---------|-----|-------------------|---------|
| Model Type | Discriminant Analysis | GLM | Discriminant Analysis |
| Approach | Models Pr[X\|Y] | Models log odds | Latent variables |
| Assumptions | Multivariate normal | Linear relationship | Linear combinations |
| Decision Boundary | Linear | Linear | Linear |
| Parameter Count | CP + P(P+1)/2 | P+1 | Depends on components |
| Collinearity | Handles correlations | Breaks down | Robust |
| Feature Selection | No inherent | With penalization | Variable importance |
| Output | Class, probability | Probability | Requires transformation |

### Use Cases

#### LDA
- When assumptions hold
- Moderate predictor count
- Correlated predictors
- Dimension reduction not needed

#### Logistic Regression
- Interpretability important
- Well-behaved predictors
- Inference needed
- Can be penalized

#### PLS-DA
- High-dimensional data
- Correlated predictors
- Predictors > samples
- Prediction focus

## Question 8: Feature Engineering and Predictor Reduction

### Feature Engineering
- Create new predictors
- Transform existing ones
- Methods:
  - Nonlinear versions
  - Splines
  - Interactions
  - Categorical encoding

### Predictor Reduction
- Remove redundant predictors
- Methods:
  - Correlation-based removal
  - Near-zero variance removal
  - Dimension reduction (PCA, PLS)
  - Built-in selection (Lasso, NSC)

## Question 9: Elastic Net in High Dimensions

### Elastic Net Structure
- Combined L1 and L2 penalties
- Formula: λ * [(1 − α) * (1/2 * Σ βj²) + α * Σ |βj|]
- Parameters:
  - λ: Total penalization
  - α: Mixing proportion

### Benefits
- Regularization
- Feature selection
- Collinearity handling
- Performance improvement

## Question 10: Time-Based Validation

### Importance
- Dynamic data distributions
- Changing relationships
- Future performance assessment
- Current environment relevance

### Challenges
- Concept drift
- Non-stationarity
- Split point selection
- Limited test data

## Question 11: Nonlinear Classification Methods

### QDA
- Class-specific covariance
- Quadratic boundaries
- More parameters
- Predictors < samples per class

### RDA
- Available in klaR package
- Modified LDA
- Handles nonlinear structures

### MDA
- Mixture of subclasses
- Flexible boundaries
- Complex distributions
- Performance varies

## Question 12: Neural Networks in Classification

### Structure
- Continuous predictions
- Softmax transformation
- Multiple classes
- Objective functions:
  - Sum of squared errors
  - Entropy

### Generalization Methods
- Weight decay
- Model averaging
- Regularization
- Parameter tuning

## Question 13: Tree-Based Methods

### CART
- Single tree
- Gini index splitting
- Cost-complexity pruning
- Class probabilities

### Bagging
- Bootstrap samples
- Multiple trees
- Voting/averaging
- Variance reduction

### Random Forests
- Random predictor selection
- Decorrelated trees
- mtry tuning
- Robust performance

### Boosting
- Sequential training
- Error correction
- Weak learners
- High performance

## Question 14: Rule-Based Models and Naïve Bayes

### Rule-Based Models
- Independent conditions
- Multiple rule triggers
- Tree-based generation
- Interpretable predictions

### Naïve Bayes
- Probabilistic classifier
- Independence assumption
- Quick computation
- Prior probabilities
- Conditional probabilities 