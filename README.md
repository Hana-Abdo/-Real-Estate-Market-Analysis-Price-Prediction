# Real Estate Market Analysis & Price Prediction

<p align="center">
  <b>Machine Learning Project for Egyptian Real Estate Price Prediction</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?logo=python">
  <img src="https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas">
  <img src="https://img.shields.io/badge/Scikit--learn-Machine%20Learning-orange?logo=scikit-learn">
  <img src="https://img.shields.io/badge/CatBoost-Regression-yellow">
  <img src="https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter">
</p>

## Overview

An end-to-end Machine Learning project for analyzing the Egyptian real estate market and predicting property prices for Sale and Rent listings.

The project covers the complete workflow from data cleaning and exploratory data analysis to feature engineering, model selection, tuning, evaluation, and price estimation.

## Highlights

* Real-world data cleaning and quality checks
* Exploratory Data Analysis
* Leakage-safe preprocessing
* Feature engineering
* Chronological Train / Validation / Test split
* Multiple regression models
* Random Forest hyperparameter tuning
* Separate Sale and Rent models
* Error analysis and feature importance
* Business-oriented property price estimator

## Workflow

```text
Raw Dataset
     |
Data Cleaning
     |
EDA & Market Analysis
     |
Feature Engineering
     |
Leakage-Safe Preprocessing
     |
Chronological Split
     |
Model Benchmarking
     |
Hyperparameter Tuning
     |
Final Model
     |
Test Evaluation
     |
Price Estimator
```

## Dataset

The dataset contains Egyptian real estate listings with information such as:

* Property type
* City / District / Subdistrict
* Area
* Bedrooms and Bathrooms
* Furnishing
* Completion status
* Property features
* Location coordinates
* Listing date
* Amenities
* Price

Target variable: `price_egp`

Sale and Rent markets are modeled separately.

## Data Preparation

Key preprocessing steps included:

* Removing duplicates and irrelevant identifiers
* Handling missing values
* Converting bedrooms and bathrooms to numeric values
* Handling `studio`, `7+`, and `none` values
* Removing invalid target prices
* Detecting invalid area values
* Cleaning rental listing inconsistencies
* Removing IDs, URLs, contact information, and other non-predictive fields

## Feature Engineering

Created features including:

* `total_rooms`
* `amenities_count`
* `area_per_bedroom`
* `bathrooms_per_bedroom`
* `log_area`
* Location interaction features
* Latitude/longitude transformations
* Listing year, month, and day of week
* Location grid features

## Preventing Data Leakage

Special attention was given to preventing target leakage.

For example, `price_per_sqm` was excluded because:

```text
price_per_sqm = price_egp / area
```

Since it directly depends on the target price, using it as a feature would leak information from the target into the model.

Preprocessing steps such as numerical imputation and categorical encoding are performed inside pipelines and learned from the training data.

## Models

The following regression models were benchmarked:

| Model             | Purpose                       |
| ----------------- | ----------------------------- |
| Linear Regression | Baseline                      |
| Random Forest     | Main tree-based model         |
| Gradient Boosting | Benchmark                     |
| CatBoost          | Categorical-feature benchmark |

The final modeling process focused on Random Forest, with targeted hyperparameter tuning.

## Validation Strategy

Instead of a random split, the project uses a chronological split:

```text
70% → Train
15% → Validation
15% → Test
```

Older listings are used for training, while newer listings are reserved for validation and final testing.

The final test set remains untouched until the final evaluation.

## Evaluation

Models are evaluated using:

* R² — primary model selection metric
* MAE — average prediction error
* RMSE — penalizes larger errors

Additional analysis includes:

* Error by price range
* Median absolute error
* Percentage of predictions within 20%
* Actual vs. predicted prices
* Feature importance

## Results

Final Sale and Rent model results are reported directly from the notebook's authoritative `final_results` table.

The final test results are intentionally not hard-coded here so that the README always reflects the latest clean notebook execution.

## Business Application

The project includes a simple property price estimator that accepts property characteristics and returns an estimated reference price in EGP.

Potential applications include:

* Buyers comparing property prices
* Investors evaluating opportunities
* Real estate market analysis
* Initial property valuation

## Tech Stack

Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, CatBoost, Jupyter Notebook, KaggleHub

## Project Structure

```text
Real-Estate-Market-Analysis/
|
├── Real_Estate_Market_Analysis.ipynb
├── README.md
└── data/
    └── propertyfinder.csv
```

Dataset files may be excluded from the repository due to size or distribution restrictions.

## Getting Started

```bash
git clone <repository-url>
cd Real-Estate-Market-Analysis
pip install pandas numpy matplotlib seaborn scikit-learn catboost kagglehub
```

Then open:

```text
Real_Estate_Market_Analysis.ipynb
```

Run the notebook from start to finish.

## Team

This project was developed collaboratively by:

* **Hana Abdo**
* **Shahd sayed**
* **ELsayed Alaa**
* **Adnan Bastawy**

### Contributions

* Data Cleaning & Preprocessing
* Exploratory Data Analysis
* Feature Engineering
* Machine Learning
* Model Evaluation
* Business Analysis

