# Module 2: Statistical Modeling and Machine Learning

## Question 1: What is Statistical Modeling?

### Definition and Overview
Statistical modeling is a mathematical model that comprises assumptions undertaken to describe the data generation process. It formalizes relationships between variables in the form of mathematical equations, where variables are stochastically related rather than deterministically.

### Formal Definition
- A statistical model is represented as a pair (𝑌, 𝑃)
  - 𝑌: Set of possible observations
  - 𝑃: Set of possible probability distributions on 𝑌
- Assumes a distinct element of 𝑃 generates the observed data
- Statistical inference enables statements about likely true elements

### Types of Statistical Models
1. **Parametric Models**
   - Make specific assumptions about population parameters
   - Collection of distributions indexed by finite-dimensional parameters

2. **Non-Parametric Models**
   - Make fewer assumptions than parametric models
   - Set of probability distributions with infinite dimensional parameters

3. **Semi-Parametric Models**
   - Combine features of both approaches
   - Have infinite dimensional parameters but not dense in distribution space

### Example: Height and Age Relationship
```python
heightᵢ = 𝑏₀ + 𝑏₁ageᵢ + 휀ᵢ
```
Where:
- 𝑏₀: Intercept
- 𝑏₁: Age parameter
- 휀: Error term
- 𝑖: Subject index

## Question 2: What is Machine Learning?

### Definition
Machine learning is a field of technology that enables computers to automatically learn from previous data. It's a scientific discipline focused on constructing and studying algorithms that can learn from data.

### Machine Learning Life Cycle
1. **Data Collection**
   - Identify data sources
   - Collect and combine data
   - Types: Primary and Secondary

2. **Data Preparation**
   - Refine and understand data
   - Explore characteristics and format
   - Pre-process for analysis

3. **Data Wrangling**
   - Convert raw data to clean data
   - Address missing values, duplicates, invalid data
   - Apply filtering techniques

4. **Data Analysis**
   - Transfer cleaned data for analysis
   - Build models and review results
   - Define problem type and choose techniques

5. **Model Training**
   - Train model with ML algorithms
   - Understand patterns and features

6. **Model Testing**
   - Check accuracy with test dataset
   - Determine accuracy percentage

7. **Deployment**
   - Deploy model in real-world system
   - Ensure acceptable speed and accuracy

### Classification of Machine Learning

#### 1. Supervised Learning
- Uses labeled training data
- Input data tagged with correct output
- Examples: Classification, Regression

#### 2. Unsupervised Learning
- Uses unlabeled dataset
- Finds underlying structure
- Examples: Clustering, Dimensionality Reduction

#### 3. Reinforcement Learning
- Feedback-based learning
- Agent learns through actions and results
- Components:
  - Agent
  - Environment
  - Actions
  - States
  - Rewards
  - Policy

## Question 3: ML Tasks Based on Desired Output

### 1. Classification
- Divides inputs into discrete classes
- Output variable is categorical
- Examples: Spam detection, Gender classification

### 2. Regression
- Predicts continuous outputs
- Examples: Weather forecasting, Market trends
- Algorithms: Linear Regression, Polynomial Regression

### 3. Clustering
- Divides inputs into groups
- Unsupervised task
- Types:
  - K-Means Clustering
  - Hierarchical Clustering
  - Density-Based Clustering
  - Spectral Clustering

### 4. Density Estimation
- Finds distribution of inputs in space

### 5. Dimensionality Reduction
- Simplifies inputs by mapping to lower dimensions
- Examples: PCA, Manifold Learning

## Question 4: ML Approaches and Applications

### Key Approaches
1. Decision Tree Learning
2. Association Rule Learning
3. Neural Networks
4. Support Vector Machines
5. Clustering
6. Bayesian Networks
7. Reinforcement Learning
8. Deep Learning

### Applications
- Computer Vision
- Natural Language Processing
- Medical Diagnosis
- Fraud Detection
- Stock Market Analysis
- Speech Recognition
- Game Playing
- Robotics
- Business Strategy
- Manufacturing

## Question 5: Standard Bayesian vs Empirical Bayes

### Key Differences
- **Standard Bayesian**: Prior distribution fixed before data observation
- **Empirical Bayes**: Prior distribution estimated from data

### Impact on Prior Distribution Estimation
- Standard Bayes: Fixed component determined externally
- Empirical Bayes: Data influences prior specification

## Question 6: Hierarchical Bayes Model

### Structure
- Multiple levels of uncertainty
- Two-stage model:
  1. Data generation from parameters
  2. Parameters drawn from population

### Hyperparameters Role
- Describe distribution characteristics
- Target of estimation in Empirical Bayes
- Used to specify prior distribution

## Question 7: EM Algorithm in Empirical Bayes

### Purpose
- Updates approximations to posterior distributions
- Iterative scheme for parameter estimation

### Contribution to Point Estimation
- Facilitates hyperparameter estimation
- Refines estimates through iteration
- Converges to likely hyperparameter values

## Question 8: Parametric vs Non-Parametric Empirical Bayes

### Comparison
| Feature | Parametric EB | Non-Parametric EB (Robbins) |
|---------|--------------|----------------------------|
| Prior Assumption | Specific parametric family | Unspecified distribution |
| Estimation Goal | Estimate hyperparameters | Point prediction without prior form |
| Methodology | MLE or Moments expansion | Empirical frequencies |
| Shrinkage Effect | Weighted average | Frequency-based adjustment |

### Preferred Scenarios for Robbins' Method
- Lack of prior knowledge
- Data-driven approach needed
- Large dataset available
- Simple structure requirements

## Question 9: Poisson-Gamma Model

### Framework Function
- Parametric forms for likelihood and prior
- Poisson distribution for likelihood
- Gamma distribution for prior
- Conjugate prior relationship

### Best Suited Data
- Count data
- Event occurrences
- Rate or intensity parameters
- Population-level variation

## Question 10: Bayesian Linear Regression

### Prior Beliefs
- Specified through prior probability distributions
- Parameters: coefficient vector and error variance
- Combines data likelihood with prior information

### Posterior Distribution Role
- Central outcome of analysis
- Combines prior beliefs with data likelihood
- Provides full probability distribution
- Enables various statistical inferences 