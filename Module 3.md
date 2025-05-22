# Module 3: Data Preprocessing and Model Evaluation

## Question 1: Data Transformation in Machine Learning

### Importance of Data Transformation
- Data pre-processing techniques involve addition, deletion, or transformation of training set data
- Can significantly impact model's predictive ability
- Different models have varying sensitivity to predictor characteristics
- Transformations can improve model performance by reducing skewness and outlier impact

### Three Key Transformation Techniques

#### 1. Centering and Scaling
- **Process**:
  - Center: Subtract average value (zero mean)
  - Scale: Divide by standard deviation (unit variance)
- **Benefits**:
  - Improves numerical stability
  - Essential for models like Partial Least Squares (PLS)
- **Limitation**: Loss of interpretability (original units lost)

#### 2. Transformations for Skewness
- **Purpose**: Remove distributional skewness
- **Types**:
  - Log transformation
  - Square root transformation
  - Inverse transformation
- **Example**: Log transformation for right-skewed actin filament intensity data

#### 3. Transformations for Outliers
- **Spatial Sign Transformation**:
  - Projects predictor values onto multidimensional sphere
  - Makes all samples equidistant from center
  - Formula: Divide each sample by its squared norm
  - Requires prior centering and scaling
  - Mitigates outlier impact while preserving relative positions

## Question 2: Skewness in Data Distribution

### Definition and Detection
- **Skewness**: Asymmetric distribution where probability of falling on either side of mean is unequal
- **Right-skewed**: More points on left (smaller values), fewer on right (larger values)
- **Detection Methods**:
  - Visual inspection using histograms
  - Calculation of skewness statistic

### Transformation Methods

#### 1. Simple Transformations
- Log transformation
- Square root transformation
- Inverse transformation

#### 2. Box-Cox Transformation
- **Formula**: x* = { (x^λ - 1) / λ if λ ≠ 0; log(x) if λ = 0 }
- **Features**:
  - Family of transformations indexed by λ
  - Includes common transformations:
    - Log (λ = 0)
    - Square (λ = 2)
    - Square root (λ = 0.5)
    - Inverse (λ = -1)
  - Optimal λ estimated via maximum likelihood
  - Applicable only to positive values

## Question 3: Principal Component Analysis (PCA)

### Overview
- Data reduction technique
- Generates smaller set of predictors capturing majority of information
- Creates surrogate variables from original predictors

### Process and Goals
- **Principal Components (PCs)**:
  - Linear combinations of predictors
  - First PC captures maximum variance
  - Subsequent PCs capture remaining variance while being uncorrelated
  - Formula: PCj = (aj1 × Predictor 1) + (aj2 × Predictor 2) + ... + (ajP × Predictor P)

### Advantages and Limitations
- **Advantages**:
  - Creates uncorrelated components
  - Improves numerical stability
- **Limitations**:
  - Unsupervised technique
  - May summarize irrelevant characteristics

### Pre-processing and Component Selection
- **Pre-processing Steps**:
  1. Transform skewed predictors
  2. Center and scale predictors
- **Component Selection**:
  - Use scree plots
  - Look for "elbow" point
  - Consider cross-validation
- **Visual Assessment**:
  - Plot first few PCs
  - Color by relevant characteristics
  - Assess data quality and clusters

## Question 4: Handling Missing Values

### Types of Missing Data
- Structurally missing
- Undetermined values
- Informative missingness (pattern related to outcome)

### Strategies

#### 1. Removal
- **When to use**:
  - Large datasets
  - Non-informative missingness
- **Considerations**:
  - Risk of data loss
  - Potential bias

#### 2. Model-based Handling
- Tree-based techniques
- Built-in missing value handling

#### 3. Imputation
- **Process**:
  - Build imputation model for each predictor
  - Fill missing values before model training
- **Popular Technique**: K-nearest neighbor
  - **Advantages**:
    - Imputed values within training range
  - **Disadvantages**:
    - Requires full training set
    - Tuning parameters needed

### Challenges
- Added uncertainty
- Computational complexity
- Need for resampling integration

## Question 5: Removing Predictors

### Reasons for Removal
1. Decreased computational complexity
2. Removal of redundant information
3. Elimination of problematic variables

### Types of Problematic Predictors

#### 1. Zero Variance Predictors
- Single unique value
- No information content
- Impact varies by model type

#### 2. Near-zero Variance Predictors
- Few unique values with low frequencies
- Single value for majority of samples
- **Diagnosis Criteria**:
  1. Small number of unique points relative to samples
  2. Large ratio of most to second most prevalent value

## Question 6: Multicollinearity

### Definition
- Collinearity: Substantial correlation between predictor pairs
- Multicollinearity: Relationships among multiple predictors

### Detection Methods

#### 1. Visualization
- Correlation matrix
- Clustered variables
- Block patterns

#### 2. PCA
- Large first component variance
- Component loadings analysis

#### 3. Variance Inflation Factor (VIF)
- Measures parameter estimate variance increase
- Limited to linear models
- Requires more samples than predictors

### Handling Methods

#### 1. Predictor Removal
- **Algorithm**:
  1. Calculate correlation matrix
  2. Find largest absolute correlation
  3. Compare average correlations
  4. Remove predictor with larger average
  5. Repeat until threshold met

#### 2. Feature Extraction
- PCA
- Other dimensionality reduction techniques

## Question 7: Adding Predictors

### Categorical Predictors
- Decomposition into specific variables
- Dummy encoding
- **Considerations**:
  - Number of dummy variables
  - Model intercept requirements
  - Tree-based model preferences

### Nonlinear Predictors
- **Manual Specification**:
  - Quadratic terms
  - Complex combinations
  - Distance metrics
- **Model-specific Considerations**:
  - Linear vs. nonlinear boundaries
  - Classification vs. regression

## Question 8: Binning Predictors

### Definition
- Converting numeric predictors into groups
- Pre-categorization before analysis

### Advantages
- Data simplification
- Improved interpretability
- Higher survey response rates
- No need for exact relationships

### Disadvantages
- Performance loss
- Precision reduction
- Higher false positive rates
- Ethical concerns in medical applications

### Important Distinction
- Manual binning vs. model-based categorization
- Statistical soundness of different approaches

## Question 9: Over-fitting

### Definition
- Model learns training data structure too well
- Includes noise in predictions
- Poor generalization to new data

### Impact
- Useless for new predictions
- Overly optimistic training performance
- Complex decision boundaries
- Parameter sensitivity

### Prevention Strategies
1. Methodological evaluation approach
2. Proper model building framework
3. Data splitting for tuning and evaluation
4. Resampling methods
5. Appropriate parameter selection
6. Preference for simpler models

## Question 10: Model Tuning

### Definition
- Process of identifying optimal parameter settings
- Uses existing data
- Focuses on realistic predictive performance

### Important Parameters

#### 1. K in KNN
- Number of nearest neighbors
- **Considerations**:
  - Too few: Over-fitting
  - Too many: Insensitive predictions

#### 2. Cost Parameter in SVM
- Price for misclassified samples
- **Effects**:
  - Large cost: Over-fitting
  - Small cost: Less aggressive model
- Additional parameter: sigma (σ) for RBF kernel

### Tuning Process
1. Define candidate values
2. Generate performance estimates
3. Choose optimal settings
4. Refit with selected parameters

## Question 11: Model Evaluation Methods

### Holdout Method
- **Process**: Single training/test split
- **When to use**:
  - Large datasets
  - Specific generalization needs
- **Challenges**:
  - Single evaluation
  - Limited uncertainty characterization
  - Training data reduction

### k-Fold Cross-Validation
- **Process**:
  - k equal-sized partitions
  - k-1 folds for training
  - One fold for testing
- **When to use**:
  - Model tuning
  - Small sample sizes
- **Advantages**:
  - Multiple performance estimates
  - Reduced bias with increasing k
- **Challenges**:
  - High variance
  - Computational cost

### Bootstrap
- **Process**:
  - Random sampling with replacement
  - Out-of-bag predictions
- **When to use**:
  - Model evaluation
  - Model comparison
- **Advantages**:
  - Low variance estimates
  - Multiple variants available
- **Challenges**:
  - Small sample instability
  - Potential bias
  - Computational intensity 