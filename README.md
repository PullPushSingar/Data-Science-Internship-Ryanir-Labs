# ✈️ Ryanair Take-Off Weight Prediction

This project aims to build a regression model for predicting the **Take-Off Weight (TOW)** of Ryanair flights based on operational flight data.

It demonstrates the full **data science pipeline**, from exploratory data analysis to preprocessing and model evaluation using multiple approaches to outlier handling.

---

## 📁 Project Structure

1. **`data/`**
   Contains both the original raw datasets (`training.csv`, `validation.csv`) and processed data used for modeling.

2. **`EDA/`**
   This folder includes multiple Jupyter notebooks used for exploratory data analysis (EDA). It covers different stages of the data lifecycle — from raw input to post-cleaning — and generates visualizations like histograms, boxplots, and distributions.

3. **`preprocessing/`**
   Contains a notebook that handles all preprocessing tasks: missing value imputation, feature engineering, encoding, and scaling.

4. **`model/`**
   Includes the model comparison notebook where multiple regression models (e.g., Linear Regression, Random Forest, XGBoost) are trained and evaluated using RMSE and MAE.

5. **`solution/`**
   Final notebook used to prepare and save predictions on the validation dataset in the required `.csv` format for submission.

---

## 📊 Features used for prediction

* `ActualFlightTime`
* `ActualTotalFuel`
* `FlownPassengers`
* `FlightBagsWeight`
* `BagsCount`

---

## 🚀 Environment Setup

This project uses **Python 3.10**.
We recommend managing dependencies using [Anaconda](https://www.anaconda.com/).

### ✅ Create and activate environment

```bash
conda create -n ryanair_regression python=3.10
conda activate ryanair_regression
pip install -r requirements.txt
```

---

## 📈 Solution Overview and Exploratory Data Analysis

### 1. Preprocessing

The first step was to understand the data. Before performing any analysis, several non-numeric and irrelevant columns were removed:

* `DepartureDate`
* `DepartureYear`
* `DepartureMonth`
* `DepartureDay`
* `FlightNumber`
* `ArrivalAirport`
* `DepartureAirport`
* `Route`

Additionally, missing values were identified in both the training and validation sets — around 3,000 missing rows in the training set and fewer than 200 in the validation set.

The missing data was saved in `/src/Data/missing_data`, then dropped from the working dataset.

Using the remaining features, various visualizations were generated: histograms, heatmaps, boxplots, and scatter plots (with `ActualTOW`).

Outliers were detected for features such as `ActualFlightTime`, `FlightBagsWeight`, `BagsCount`, and `ActualTotalFuel`. These values were restricted to the following ranges:

* `ActualFlightTime`: 10–500
* `ActualTotalFuel`: 500–14,000
* `FlownPassengers`: 0–200
* `FlightBagsWeight`: 0–3,000
* `BagsCount`: 0–300
* `ActualTOW`: 50,000–75,000

After cleaning, the distributions were re-evaluated — no additional anomalies were observed.

Correlation heatmaps revealed a strong relationship between most features and the target variable `ActualTOW`.

Missing values were imputed using the **K-Nearest Neighbors (KNN)** algorithm.

Final, cleaned datasets were saved as:

* Training set: `/src/Data/processed/training_full.csv`
* Validation set: `/src/Data/processed/validation_full.csv`

Post-cleaning comparison showed that both training and validation histograms were well-aligned, indicating consistent data distribution after removing extreme outliers.

Additional engineered features were briefly tested, but some of them resulted in negative `ActualTOW` predictions and were thus discarded.

---

### 2. Model Selection

After imputing the missing values, several regression models were trained and evaluated:

* Linear Regression
* Decision Tree
* Random Forest
* XGBoost
* Voting Regressor (combining LR, RF, XGB)
* Stacking Regressor (LR, RF, XGB)

The best results were achieved using the **Voting Regressor** (combining Linear Regression, Random Forest, and XGBoost), which was ultimately selected for final prediction.

---

### 3. Generating Predictions

The final CSV file — based on `validation.csv` with added predicted `ActualTOW` — is saved at:

* `/src/Data/solution/validation_predictions.csv`

Additionally, two helper files are included in the same folder:

* `validation_predictions_only_ActualTOW.csv`: contains only the predicted `ActualTOW` values
* `validation_full_with_predictions.csv`: full validation data with predicted `ActualTOW`

---

## 👨‍💼 Author - Hubert Kowalczyk

Prepared as part of a recruitment task for **Ryanair Labs — Data Science Internship**.
