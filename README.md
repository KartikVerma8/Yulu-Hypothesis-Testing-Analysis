# Yulu-Hypothesis-Testing-Analysis

## 📌 Table of Contents

- [Overview](#overview)
- [Business Problem](#business-problem)
- [Dataset](#dataset)
- [Tools & Technologies](#tools--technologies)
- [Project Structure](#project-structure)
- [Data Cleaning & Preparation](#data-cleaning--preparation)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Research Questions & Key Findings](#research-questions--key-findings)
- [Analysis & Statistical Testing](#analysis--statistical-testing)
- [How to Run This Project](#how-to-run-this-project)
- [Final Recommendations](#final-recommendations)
- [Author & Contact](#author--contact)

---

## Overview

This project analyzes Yulu's shared electric bike rental demand using Python, Exploratory Data Analysis (EDA), and statistical hypothesis testing.

The objective is to understand the factors influencing rental demand and investigate whether differences in bike rentals across working days, seasons, and weather conditions are statistically significant.

The project combines data cleaning, data visualization, correlation analysis, and hypothesis testing to generate meaningful insights and support data-driven business decisions.

### 🏆 Project Achievement

**Scored 88/100 in the Scaler Yulu Hypothesis Testing Case Study.**

This project demonstrates the practical application of Python-based data analysis, exploratory data analysis, statistical hypothesis testing, and data-driven business recommendations to understand bike rental demand.

## Business Problem

Yulu, an Indian micro-mobility service provider, wants to understand the factors influencing demand for its shared electric cycles.

The business needs to investigate changes in rental demand and understand how weather conditions, seasons, and working days relate to the number of rentals.

The objective of this analysis is to answer key business questions and support better demand forecasting, fleet allocation, and operational planning.

Key business questions include:

- Does rental demand differ between working and non-working days?
- Does rental demand vary significantly across seasons?
- How do different weather conditions relate to bike rental demand?
- Which environmental factors are associated with higher or lower rental demand?
- How can statistical analysis help improve operational decision-making?

## Dataset

- **Business:** Yulu
- **Dataset Type:** Bike rental demand data
- **Format:** Text/CSV-style dataset
- **Number of Records:** 10,886
- **Time Period:** January 2011 to December 2012
- **Target Variable:** `count` — total bike rentals

### Key Dataset Features

| Feature | Description |
|---|---|
| `datetime` | Date and hour of observation |
| `season` | Season category |
| `holiday` | Indicates whether the observation falls on a holiday |
| `workingday` | Indicates whether the day is a working day |
| `weather` | Weather condition category |
| `temp` | Temperature |
| `atemp` | Feeling temperature |
| `humidity` | Humidity level |
| `windspeed` | Wind speed |
| `casual` | Rentals by casual users |
| `registered` | Rentals by registered users |
| `count` | Total bike rentals |

The dataset was loaded into Python for data cleaning, exploratory analysis, visualization, and statistical hypothesis testing.

*Note: Add the original dataset source URL after verifying it from your Scaler notebook or assignment materials.*

## Tools & Technologies

- **Python:** Data analysis and statistical computations
- **Pandas:** Data manipulation and cleaning
- **NumPy:** Numerical operations
- **Matplotlib:** Data visualization
- **Seaborn:** Statistical plots and visual analysis
- **SciPy:** Statistical hypothesis testing
- **Google Colab:** Notebook development and execution

## Project Structure

The following is a suggested repository structure for GitHub.

```text
Yulu-Hypothesis-Testing-Analysis/
│
├── Yulu_Hypothesis_Testing.ipynb
├── README.md
│
├── data/
│   └── Yulu.txt
│
└── images/
    ├── rental_distribution.png
    ├── correlation_heatmap.png
    ├── rental_by_season.png
    └── rental_by_weather.png
```

*Update the filenames to match the actual files you upload. Include the dataset only if its license permits redistribution.*

## Data Cleaning & Preparation

Data preparation was performed using Pandas before conducting exploratory and statistical analysis.

The major steps included:

1. **Data Loading:** Imported the dataset into a Pandas DataFrame.
2. **Data Profiling:** Examined dataset dimensions, column names, data types, and memory usage.
3. **Date Conversion:** Converted the `datetime` column into an appropriate datetime format.
4. **Categorical Conversion:** Converted relevant variables, including `season`, `holiday`, `workingday`, and `weather`, into categorical data types.
5. **Missing Value Analysis:** Checked for null values across the dataset.
6. **Descriptive Statistics:** Used summary statistics to understand numerical variables.
7. **Unique Value Analysis:** Examined unique values and category distributions.
8. **Outlier Detection:** Used boxplots and the Interquartile Range (IQR) method to identify potential outliers.
9. **Data Validation:** Reviewed distributions and relationships before statistical testing.

Potential outliers were investigated rather than automatically removed, as unusually high rental counts may represent genuine periods of high demand.

## Exploratory Data Analysis (EDA)

Exploratory data analysis was performed to understand rental demand patterns and relationships among the variables.

### 1. Univariate Analysis

- Analyzed numerical distributions using histograms and KDE plots.
- Examined categorical distributions using count plots.
- Investigated casual, registered, and total rental distributions.
- Identified skewness and unusual observations in rental-count variables.

### 2. Outlier Analysis

The IQR method identified the following potential outliers in the dataset.

| Variable | Potential Outliers | Percentage |
|---|---:|---:|
| Temperature | 0 | 0.00% |
| Feeling Temperature | 0 | 0.00% |
| Humidity | 22 | 0.20% |
| Wind Speed | 227 | 2.09% |
| Casual Rentals | 749 | 6.88% |
| Registered Rentals | 423 | 3.89% |
| Total Rentals | 300 | 2.76% |

These observations were treated as potential outliers and retained for analysis rather than automatically removed.

### 3. Correlation Analysis

A correlation heatmap was used to examine relationships between numerical variables.

Key observations included:

- Total rentals had a strong positive correlation with registered rentals.
- Total rentals had a moderate positive correlation with casual rentals.
- Temperature had a positive correlation with total rentals.
- Humidity had a negative correlation with total rentals.
- Temperature and feeling temperature were highly correlated.

Since total rentals equal casual rentals plus registered rentals, their correlations with total rentals are partly driven by this mathematical relationship and should not be interpreted as independent predictive relationships.

## Research Questions & Key Findings

### Research Questions

1. Does average rental demand differ between working and non-working days?
2. Does rental demand differ significantly across seasons?
3. Is rental demand associated with different weather conditions?
4. Which environmental factors are associated with higher or lower rental demand?
5. How can the findings support demand forecasting and operational planning?

### Key Findings

#### 1. Working Days vs. Non-Working Days

- Mean rentals on working days: approximately **193.01**.
- Mean rentals on non-working days: approximately **188.51**.
- Independent two-sample t-test p-value: approximately **0.2264**.

At a 5% significance level, the analysis did not find sufficient evidence of a difference in mean rental demand between working and non-working days.

#### 2. Seasonal Rental Demand

| Season | Approximate Mean Rentals |
|---|---:|
| Spring | 116.34 |
| Summer | 215.25 |
| Fall | 234.42 |
| Winter | 198.99 |

- Fall had the highest average rental count.
- Spring had the lowest average rental count.
- One-way ANOVA produced an F-statistic of approximately **236.95**, with a p-value below 0.05.

The analysis provides strong evidence that mean rental demand differs across seasons.

#### 3. Weather and Rental Demand

| Weather Category | Approximate Mean Rentals |
|---|---:|
| Category 1 | 205.24 |
| Category 2 | 178.96 |
| Category 3 | 118.85 |

The descriptive results indicate lower average rental demand under less favorable weather conditions.

Weather Category 4 contained only one observation, so its mean should be interpreted cautiously. A suitable statistical test is needed to establish whether differences across weather categories are statistically significant.

## Analysis & Statistical Testing

Statistical hypothesis testing was used to determine whether observed differences in rental demand were statistically significant.

### 1. Working Days vs. Non-Working Days

**Test:** Independent two-sample t-test

**Hypotheses**

- **Null hypothesis (H₀):** Mean rental demand is equal on working and non-working days.
- **Alternative hypothesis (H₁):** Mean rental demand differs between working and non-working days.

**Significance level:** 0.05

| Metric | Result |
|---|---:|
| Mean rentals on working days | 193.01 |
| Mean rentals on non-working days | 188.51 |
| Levene's test p-value | 0.9438 |
| T-test p-value | 0.2264 |

**Conclusion:** Fail to reject the null hypothesis because the p-value exceeds 0.05. The analysis does not provide sufficient statistical evidence of a difference in mean rental demand between working and non-working days.

### 2. Seasonal Rental Demand

**Test:** One-way ANOVA

**Hypotheses**

- **Null hypothesis (H₀):** Mean rental demand is equal across all four seasons.
- **Alternative hypothesis (H₁):** At least one season has a different mean rental demand.

**Significance level:** 0.05

| Metric | Result |
|---|---:|
| F-statistic | Approximately 236.95 |
| P-value | Approximately \(6.16 \times 10^{-149}\) |

**Conclusion:** Reject the null hypothesis. There is strong statistical evidence that mean rental demand differs across seasons.

**Statistical limitation:** Levene's test indicated unequal variances across seasons. Therefore, the classical ANOVA result should be interpreted with caution. Welch's ANOVA can be considered as an alternative when group variances are unequal.

### 3. Weather and Rental Demand

The project compares rental counts across weather categories using descriptive statistics and visualizations.

The observed averages suggest that rental demand decreases under less favorable weather conditions. However, the weather-related statistical conclusion should be based on the test results in the notebook, accounting for the very small number of observations in Category 4.

## How to Run This Project

1. Clone or download this GitHub repository.
2. Download the dataset from the `data` folder, if included.
3. Open [Google Colab](https://colab.research.google.com/).
4. Upload `Yulu_Hypothesis_Testing.ipynb` or open it directly from GitHub.
5. Upload the dataset to the Colab session or mount Google Drive.
6. Update the dataset file path in the notebook, if necessary.
7. Install any missing Python dependencies, if required.
8. Execute the notebook cells in sequence to reproduce the analysis, visualizations, and statistical tests.

**Note:** If your notebook references `/content/Yulu.txt`, ensure that the dataset is uploaded to that location or update the path accordingly.

## Final Recommendations

Based on the observed analysis, the following recommendations can support Yulu's operational planning.

- **Plan for seasonal demand:** Investigate additional fleet availability during higher-demand seasons such as Fall.
- **Adjust for lower-demand periods:** Review fleet allocation, maintenance schedules, and operating capacity during lower-demand seasons such as Spring.
- **Monitor weather conditions:** Incorporate weather information into short-term demand forecasting and operational planning.
- **Avoid assumptions about working days:** The current analysis did not find sufficient evidence of a difference in mean rental demand between working and non-working days.
- **Improve statistical validation:** Use statistical methods that account for unequal variances and investigate the effect of the very small fourth weather category.
- **Explore demand forecasting:** Consider seasonality, time of day, temperature, humidity, weather, and historical rentals as potential model features.
- **Track business KPIs:** Monitor rental volume, bike availability, forecast accuracy, and revenue to evaluate operational improvements.

These recommendations should be validated against additional operational and revenue data before implementation.

## Author & Contact

**Kartik Verma**

- **GitHub:** [KartikVerma8](https://github.com/KartikVerma8)
- **LinkedIn:** Add your LinkedIn profile URL

---

*This project was completed as part of the Scaler learning journey. The case study received a score of 88/100.*
