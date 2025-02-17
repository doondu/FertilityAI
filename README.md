# FertilityAI: Predicting Pregnancy Success  

## Introduction  
This project aims to predict pregnancy success based on fertility-related data using various machine learning models.  

## Dataset  
- The dataset consists of categorical and boolean features.  
- Feature selection was performed using multiple techniques, including SVM, PCA, LightGBM, Correlation, and Mutual Information.  

## Feature Selection  
Feature selection was conducted to identify the most relevant features for model training. The following methods were used:  
- **SVM-based Feature Selection**  
- **Principal Component Analysis (PCA)**  
- **LightGBM Feature Importance**  
- **Correlation Analysis**  
- **Mutual Information**  

## Model Training & Evaluation  
After feature selection, various models were trained and evaluated using:  
- **Precision**  
- **Recall**  
- **F1-score**  
- **ROC-AUC Score**  

## Feature Engineering (Planned)  
- Further feature engineering will be conducted based on model performance.  
- Techniques such as feature transformation, interaction features, and outlier handling will be explored.  

## Results & Insights  
- The impact of selected features on model performance.  
- Comparison of different machine learning models.  

## How to Run  
```bash
git clone https://github.com/your-repo/FertilityAI.git  
cd FertilityAI  
pip install -r requirements.txt  
python train.py
```

## Future work
- Hyperparameter tuning for improved model performance.
- Exploration of deep learning techniques.
- Integration of additional clinical data.

## Referneces
- [Reference 1]
- [Reference 2]
