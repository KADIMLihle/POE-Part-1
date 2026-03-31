# POE Part 1: Medical Insurance Cost Prediction

## Project Overview

This project develops a linear regression model to predict medical insurance charges based on customer demographic and lifestyle factors. The analysis was conducted for a medical aid scheme to support the development of a sliding-scale pricing structure.

## Repository Structure

```
├── PDAN8411_POE_Part1_Kadi.ipynb   # Main Jupyter notebook with complete analysis
├── PDAN8411_POE_Part1_Kadi.pdf     # Final report with findings and recommendations
├── eda_visualizations.png          # Exploratory data analysis plots
├── model_performance.png           # Model evaluation visualizations
├── insurance.csv                   # Dataset used for analysis
└── README.md                       # This file
```

## Dataset

The dataset used is the "Medical Cost Personal Datasets" from Kaggle, containing 1,338 customer records with the following features:

| Feature | Type | Description |
|---------|------|-------------|
| age | Numerical | Beneficiary's age (18-64 years) |
| sex | Categorical | Gender (male/female) |
| bmi | Numerical | Body Mass Index (15.96 - 53.13) |
| children | Numerical | Number of dependents (0-5) |
| smoker | Categorical | Smoking status (yes/no) |
| region | Categorical | Geographic region (northeast, northwest, southeast, southwest) |
| charges | Numerical | Individual medical costs billed (target variable) |

## Key Findings

### Model Performance
- **Test R²**: 0.85 (85% of variance explained)
- **RMSE**: $5,180 (average prediction error)
- **MAE**: $3,610 (average absolute error)
- **MAPE**: 28.1% (average percentage error)

### Top Predictors
| Feature | Coefficient | Impact |
|---------|-------------|--------|
| smoker_yes | +$23,612 | Highest impact |
| age | +$256 | High impact per year |
| bmi | +$332 | High impact per unit |
| age_smoker | +$340 | Medium impact (interaction) |
| bmi_smoker | +$380 | Medium impact (interaction) |
| children | +$432 | Medium impact |

## Requirements

To run the notebook, you'll need the following Python packages:

```
pandas
numpy
matplotlib
seaborn
scikit-learn
statsmodels
```

## Installation

1. Clone this repository:
```bash
git clone <repository-url>
```

2. Install required packages:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels
```

3. Run the Jupyter notebook:
```bash
jupyter notebook PDAN8411_POE_Part1_Kadi.ipynb
```

## Methodology

### 1. Data Preprocessing
- Removed duplicate records
- Performed train-test split (80/20)
- Applied One-Hot Encoding to categorical variables
- Created interaction terms (age × smoker, bmi × smoker)

### 2. Model Development
- Initial linear regression model with main effects
- Improved model with interaction terms to capture amplified effects for smokers

### 3. Model Evaluation
- R² (coefficient of determination)
- RMSE (Root Mean Square Error)
- MAE (Mean Absolute Error)
- MAPE (Mean Absolute Percentage Error)
- Residual analysis

## Key Visualizations

The analysis includes six EDA visualizations:
1. Distribution of medical charges
2. Charges by smoking status (boxplot)
3. Age vs charges by smoking status (scatter plot)
4. BMI vs charges by smoking status (scatter plot)
5. Charges by geographic region (boxplot)
6. Correlation matrix heatmap

Model evaluation visualizations include:
- Actual vs predicted scatter plot
- Residual plot
- Residual distribution histogram

## Business Recommendations

1. **Implement Smoking-Based Pricing**: Apply $23,600 surcharge for smokers
2. **Develop Age-Based Sliding Scale**: Age effects compound with smoking status
3. **Incentivize Healthy BMI**: Each BMI point reduction saves approximately $330 annually
4. **Simplify Regional Pricing**: Regional differences are minimal (<$500)

## Limitations

- US-based dataset may not generalize to South African market
- Linear assumptions (validated through EDA)
- Limited features (no medical history, chronic conditions)
- No time dimension for premium changes over time

## Future Improvements

- Collect South African customer data for calibration
- Add medical history features (chronic conditions, prior claims)
- Explore non-linear models (Random Forest, XGBoost)
- Implement k-fold cross-validation
- Create additional interaction terms

## Author

**Kadimetjang Mphahlele**  
Student Number: ST10496571  
Programming for Data Analytics 1

## References

- Kaggle. (n.d.). Medical Cost Personal Datasets. Retrieved from https://www.kaggle.com/datasets/mirichoi0218/insurance
- Pedregosa, F., et al. (2011). Scikit-learn: Machine Learning in Python. Journal of Machine Learning Research, 12, 2825-2830.
- Waskom, M. L. (2021). Seaborn: statistical data visualization. Journal of Open Source Software, 6(60), 3021.
- Hunter, J. D. (2007). Matplotlib: A 2D graphics environment. Computing in Science & Engineering, 9(3), 90-95.
- McKinney, W. (2010). Data Structures for Statistical Computing in Python. Proceedings of the 9th Python in Science Conference, 51-56.
