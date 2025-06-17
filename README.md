# Predicting IVF Success  
- This project was developed for the **LG AI Research** Institute's fertility prediction hackathon, utilizing state-of-the-art gradient boosting models combined with blending techniques.
- Referneces: [*An Integrated Optimization and Deep Learning Pipeline for Predicting Live Birth Success in IVF Using Feature Optimization and Transformer-Based Models*](https://arxiv.org/pdf/2412.19696)

<br>

### Project Overview

- This project addresses the critical medical challenge of predicting IVF success rates to optimize treatment decisions.
- By leveraging a comprehensive dataset of 346,418 fertility treatment records (256,351 training, 90,067 test samples), we developed an advanced ensemble learning system that combines multiple gradient boosting models through optimized blending techniques.
- The model achieved performance within the ***top 26%*** of all participants based on the competition results

<br>

### Data Preprocessing

#### 1. Dropping Irrelevant Columns
The columns `'임신 시도 또는 마지막 임신 경과 연수'`, `'PGD 시술 여부'`, and `'PGS 시술 여부'` were removed due to irrelevance or high missingness.

#### 2. Handling Boolean Columns
Several binary categorical columns (e.g., `'배란 자극 여부'`, `'단일 배아 이식 여부'`) are converted to `bool` type for model compatibility. NaN values in selected boolean columns are retained or addressed explicitly.

#### 3. Converting Categorical to Numeric
- Columns indicating counts (e.g., `'총 시술 횟수'`, `'총 임신 횟수'`) are cleaned by removing the '회' suffix and converting `'6 이상'` to 6, then cast to integers.
- Categorical codes (e.g., `'시술 시기 코드'`, `'시술 유형'`, `'시술 당시 나이'`) are mapped to integers using predefined dictionaries.

<br>

### Model Architecture
#### Base Models Selection

Our ensemble leverages four complementary gradient boosting algorithms, each contributing unique strengths:

**1. LightGBM**
- Gradient-Based One-Sided Sampling (GOSS) for efficient training
- Superior performance on large-scale datasets
- Memory efficiency and fast inference

**2. CatBoost**
- Native categorical feature handling without preprocessing
- Built-in overfitting protection through ordered boosting
- Robust default parameters reducing tuning requirements

**3. XGBoost**
- Industry-standard gradient boosting with extensive optimization
- Strong performance on structured data
- Comprehensive hyperparameter control

**4. RandomForest**
- Ensemble diversity through bagging and random feature selection
- Natural overfitting resistance
- Interpretability through feature importance analysis

<br>

### Model Training & Blending Strategy
#### 1. Hyperparameter Optimization
Two methods were used to tune model parameters:
- Optuna was used to find the best hyperparameters for the XGBoost model by maximizing the ROC-AUC score.

- Bayesian Optimization using BayesSearchCV was applied to several models including RandomForest, LightGBM, and CatBoost for more refined tuning.

#### 2. Model Blending (Stacking)
After identifying the best-performing hyperparameters (mainly from Bayesian Optimization), a StackingClassifier was constructed using:

- Base learners: RandomForestClassifier, LGBMClassifier, and CatBoostClassifier (all optimized).

- Final estimator: LogisticRegression.

#### 3. Final Evaluation
The final stacked model was evaluated using multiple metrics, including:

```
Accuracy, Precision, Recall, F1-score, ROC-AUC
```

This approach allowed for robust ensemble learning by leveraging the strengths of multiple tree-based models with optimized settings.
