# PowerCo Customer Churn Analysis

Customer churn analysis for a mid-sized European energy provider (PowerCo), completed as part of the **BCGX Data Science job simulation** (via Forage).

## Business Problem

PowerCo, a major gas and electricity utility, has been losing customers to competitors at a growing rate — particularly since the liberalization of the European energy market made it easier for customers to switch providers. The commercial team suspects that **price sensitivity** is a major driver of churn and asked for a data-driven investigation: is churn actually driven by price, and can we predict which customers are at risk of leaving?

This repo covers my end-to-end approach to that problem, structured around a standard data science workflow: business understanding → data cleaning & EDA → feature engineering → modeling → insights & recommendations.

## Data

Two raw datasets were provided:
- `client_data.csv` — customer-level information: contract dates, consumption, pricing, margins, churn status
- `price_data.csv` — monthly historical pricing (peak/off-peak/mid-peak, variable and fixed components) per customer

Processed outputs:
- `clean_data_after_eda.csv` — cleaned dataset after exploratory analysis (handling missing values, fixing data types, treating outliers)
- `clean_data_after_feature_engineering.csv` — final dataset with engineered features, ready for modeling

## Approach

### 1. Exploratory Data Analysis (`notebooks/1_eda.ipynb`)
- Explored distributions of consumption, pricing, and contract-related variables
- Investigated the relationship between churn and categorical variables (e.g. sales channel)
- Identified and handled missing values, incorrect data types, and outliers
- Visualized churn proportions across customer segments to surface early patterns

### 2. Feature Engineering (`notebooks/2_feature_engineering.ipynb`)
- Removed redundant columns (e.g. duplicate margin columns)
- Engineered a price-sensitivity feature: the change in off-peak energy and power prices between January and December, testing the hypothesis that customers facing bigger price increases are more likely to churn
- Extracted date-based features: contract tenure in months, months since last product modification, months to/since renewal, and signup year/month (to capture seasonality)
- Created a flag for whether a customer's product had ever been modified since signup
- Built consumption-based features: actual vs. forecasted consumption gap, and average monthly consumption normalized by tenure

### 3. Modeling *(in progress)*
Next step: train a classification model (e.g. Random Forest) to predict churn using the engineered features, and evaluate performance.

### 4. Insights & Recommendations *(coming soon)*
Final step: translate model results (including feature importance) into a business recommendation on whether — and how — a price-based retention strategy should be targeted.

## Tools
Python, Pandas, Jupyter Notebook

## Status
✅ EDA complete | ✅ Feature Engineering complete | 🔲 Modeling | 🔲 Insights & Recommendations

---
*This project was completed as part of the BCGX Data Science job simulation on Forage, using a business case modeled on a real-world energy retailer.*
