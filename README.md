# Air Quality Regression Analysis

Academic machine learning project completed as part of the Master's program in Mathematics and Applications at Sorbonne University.

## Project overview

This project studies the **UCI Air Quality dataset**, which contains hourly measurements of atmospheric pollution, chemical sensor responses and meteorological variables.

The objective is to compare several statistical learning methods on a regression problem and evaluate their ability to predict pollutant concentrations.

The main target variables are:

- `CO(GT)`
- `C6H6(GT)`
- `NOx(GT)`
- `NO2(GT)`

They are predicted using chemical sensor responses (`PT08.*`) and meteorological variables such as temperature and humidity.

## Main steps

The notebook covers the complete analytical workflow:

- Data loading and cleaning
- Missing-value analysis
- Exploratory data analysis
- Correlation analysis
- Temporal analysis
- Train/test split respecting chronological order
- Feature scaling
- Hyperparameter tuning
- Model comparison
- Critical analysis of results

## Models compared

Several regression approaches are implemented and compared:

- Ordinary Least Squares
- Ridge Regression
- Lasso Regression
- Elastic Net
- Kernel Ridge Regression with RBF kernel
- Multi-Layer Perceptron
- Regressor Chain
- Random Forest
- XGBoost

Hyperparameters are selected using **TimeSeriesSplit** when appropriate in order to preserve the chronological structure of the data.

## Missing data strategy

Several strategies were compared:

- dropping incomplete observations
- mean imputation
- median imputation
- linear interpolation

In this dataset, removing incomplete observations provided the best overall results, mainly because many missing values correspond to common sensor interruptions rather than random isolated measurements.

## Evaluation metrics

The models are evaluated using:

- RMSE
- MAE
- R²

This makes it possible to compare both predictive accuracy and robustness to large errors.

## Main results

The non-linear models generally outperform the linear approaches.

The best-performing models include:

- **Kernel Ridge** for `CO(GT)`
- **Kernel Ridge / MLP** for `C6H6(GT)`
- **Kernel Ridge / MLP** for `NOx(GT)`
- **MLP** for `NO2(GT)`

Kernel Ridge provides the best overall compromise on the dataset, with an average R² around 0.84.

The analysis also shows that `NO2(GT)` is the most difficult target to predict, while `C6H6(GT)` is predicted almost perfectly due to its very strong relationship with one of the chemical sensors.

## Key methodological points

- Chronological train/test split
- TimeSeriesSplit for hyperparameter selection
- Standardization inside sklearn pipelines
- Comparison of linear and non-linear approaches
- Analysis of multicollinearity
- Evaluation of feature selection through Lasso and Elastic Net
- Critical discussion of temporal distribution shift and extreme pollution events

## Tools

- Python
- pandas
- NumPy
- scikit-learn
- matplotlib
- seaborn
- XGBoost
- Jupyter Notebook

## Repository structure

```text
air-quality-regression-analysis/
├── air_quality_regression_analysis.ipynb
└── README.md
