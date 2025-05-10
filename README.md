# ✈️ Ryanair Take-Off Weight Prediction

This project aims to build a regression model for predicting the **Take-Off Weight (TOW)** of Ryanair flights based on operational flight data.

It demonstrates the full **data science pipeline**, from exploratory data analysis to preprocessing and model evaluation using multiple approaches to outlier handling.

---

## 📁 Project Structure

```
.
├── data/                      # Raw and processed CSV data
│   ├── training.csv
│   ├── validation.csv
│   └── processed/             # Cleaned, winsorized, and IQR-based datasets
├── notebooks/                
│   ├── EDA/                   # Exploratory Data Analysis
│   │   └── EDA_visualization.ipynb
│   ├── DataPreprocessing/    # Data cleaning and outlier handling
│   │   ├── cleaning_missing_data.ipynb
│   │   ├── outlier_remobal_iqr.ipynb
│   │   └── winsorization.ipynb
│   └── Models/               # Model training and comparison
│       └── model_trainng_comprasion.ipynb
├── requirements.txt
└── README.md
```

---

## 📊 Features used for prediction

- `ActualFlightTime`
- `ActualTotalFuel`
- `FlownPassengers`
- `FlightBagsWeight`
- `BagsCount`
- (optionally: route/airport data as categorical features)

---

## 🚀 Steps completed

- Exploratory Data Analysis (EDA)
- Handling missing values
- Outlier treatment:
  - Baseline (no outlier handling)
  - IQR-based outlier removal
  - Winsorization
- Linear regression model training and performance comparison (RMSE, MAE)

---

## 🔧 Environment Setup

This project uses **Python 3.10**.  
We recommend managing dependencies using [Anaconda](https://www.anaconda.com/).

### ✅ Create and activate environment

```bash
conda create -n ryanair_regression python=3.10
conda activate ryanair_regression
pip install -r requirements.txt
```

---

## 📈 Planned Extensions

- Add Ridge, Lasso, and XGBoost regressors
- Residuals analysis
- Feature engineering for route/airport data

---

## 👨‍💻 Author

Prepared as part of a recruitment task for **Ryanair Labs — Data Science Internship**.
