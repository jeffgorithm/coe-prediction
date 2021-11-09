# COE Price Prediction
## About
A Certificate of Entitlement (COE) gives a Singaporean citizen the right to own and use a vehicle in Singapore. For this project, I attempt to apply statistical and machine learning techniques to model and predict COE prices.

## Data Sources
1. [COE Prices (Monthly)](https://coe.sgcharts.com/)
2. [Vehicle Population (Monthly)](https://www.singstat.gov.sg/find-data/search-by-theme/industry/transport/latest-data)
3. [Consumer Price Index (Monthly)](https://www.singstat.gov.sg/find-data/search-by-theme/industry/finance-and-insurance/latest-data)

## Directory Structure

```
│   README.md
│   requirements.txt
|   environment.yml
|
└───data
│   │   coe_prices.csv
│   │   vehicle_population.csv
│   │   cpi.csv
│   │   ...
│   
└───notebooks
    │   EDA.ipynb
    │   Feature Engineering.ipynb
    │   Modeling.ipynb
```

## Getting Started

### Prerequisites
Make sure you have the following installed:
1. Python 3
2. Anaconda
3. Jupyter Notebook

### Create Conda Environment with required packages
```
conda env create -f environment.yml
```

### Activate Conda Environment
```
conda activate coe
```

### Start Jupyter Notebook
```
jupyter notebook
```

### Notebook Sequence
1. EDA.ipynb - Data Exploration and Fusion
2. Feature Engineering.ipynb - Generating new features
3. Modeling.ipynb - Experimenting with various ML Models

## Main Techniques Applied

### Data Pre-processing
- Merging multiple data sources (COE Price, vehicle population and CPI(Transport and Car indices))
- Box-Cox Transformation for transforming output variable (price) distribution
- MinMaxScaler for numerical features
- One-hot encoding for categorical features (Unified Model vs Category Specific Models)

### Feature Selection
- Applied Recursive Feature Elimination (RFE) to find best subset of features

### Hyperparameter Tuning
- Applied GridSearch Cross Validation to find best parameters

### Machine Learning
- Linear Regression
- Lasso Regression
- Ridge Regression
- k-Neighbors Regression
- Decision Tree Regression
- Random Forest Regression
- Multi-layer Perceptron

### Evaluation/Validation
- Trained models with k-fold cross validation

## Results
| Model|Unified (MAE)|Unified (RMSE)|Cat A (MAE)|Cat A (RMSE)|Cat B (MAE)|Cat B (RMSE)|
|---|---|---|---|---|---|---|
| LR            |2866|3881|2108|2633|2349|3489|
| Lasso         |2849|3845|2179|2707|2317|3478|
| Ridge         |3495|4411|2108|2633|2349|3489|
| ElasticNet    |2849|3845|2179|2707|2317|3478|
| Decision Tree |4567|6068|3403|4671|3391|4679|
| Random Forest |2532|3411|2113|2750|2352|3276|
| MLP           |**1703**|**2231**|**1432**|**1845**|**1777**|**2466**|
