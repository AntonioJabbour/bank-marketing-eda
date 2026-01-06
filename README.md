# Bank Marketing Campaign – Exploratory Data Analysis (EDA)

## Overview

This project analyzes a bank marketing campaign dataset to understand **which customer segments are most likely to subscribe to a term deposit**.  
The main focus is on **Exploratory Data Analysis (EDA)**: cleaning the data, exploring patterns, and generating business‑oriented insights for marketing.

This project was completed as part of my data science learning path after finishing the IBM Data Science Professional Certificate.

---

## Dataset

- **Source:** Bank marketing dataset (Portuguese bank) – available on Kaggle / UCI Machine Learning Repository  
- **Rows:** ~11,000 customers  
- **Target variable:** `deposit`  
  - `yes` – client subscribed to a term deposit  
  - `no` – client did not subscribe  

**Key features (examples):**

- **Client profile:** `age`, `job`, `marital`, `education`, `balance`, `housing`, `loan`
- **Campaign contact info:** `contact` (cellular / telephone), `month`, `day`, `duration`, `campaign`
- **Previous campaign info:** `pdays`, `previous`, `poutcome` (previous outcome)

---

## Objectives

1. Assess the **overall performance** of the campaign (subscription rate).
2. Identify **which customer segments** (age, job, education, marital status) respond better.
3. Compare the effectiveness of different **contact channels** (cellular vs telephone).
4. Analyze the impact of **previous campaign outcomes** on current subscription behavior.
5. Provide **data‑driven recommendations** to improve future marketing campaigns.

---

## Methods

All analysis was carried out in **Python** using **Jupyter/Colab**.

Main steps:

1. **Data Loading & Inspection**
   - Loaded the CSV into a Pandas DataFrame.
   - Checked shape, data types, missing values, and duplicates.

2. **Data Cleaning**
   - Confirmed there were **no missing values** and **no duplicate rows**.
   - Treated `"unknown"` values in categorical variables as a separate category.
   - Created helper features:
     - `age_group`: binned ages into `<30`, `30–40`, `40–50`, `50+`.
     - `deposit_flag`: numeric flag (1 if `deposit == "yes"`, else 0) for easier aggregation.

3. **Exploratory Data Analysis (EDA)**
   - **Univariate analysis:** distributions of age, job, marital status, education, contact type, and previous outcome (`poutcome`).
   - **Bivariate analysis with target (`deposit_flag`):**
     - Conversion rate by **age group**
     - Conversion rate by **job type**
     - Conversion rate by **contact method**
     - Conversion rate by **marital status**
     - Conversion rate by **education level**
     - Conversion rate by **previous campaign outcome (`poutcome`)**
   - Visualizations created using **Matplotlib** and **Seaborn** (bar plots, count plots, etc.).
   - All major plots include short written interpretations.

---

## Key Findings

> Note: percentages are approximate and based on this dataset version.

- **Overall subscription rate**
  - About **47%** of customers subscribed to the term deposit; **53%** did not.

- **Age groups**
  - Most customers are between **30–40** years old, followed by **40–50** and **50+**; the **<30** group is the smallest.
  - Conversion rates are **higher** for the **<30** and **50+** age groups, while **30–40** and **40–50** convert slightly below average.

- **Job type**
  - The campaign mainly reaches customers in **management**, **blue‑collar**, and **technician** roles.
  - The highest conversion rates are observed for:
    - **Students** (~75%)
    - **Retired** customers (~66%)
    - **Unemployed** customers (~57%)
    - **Management** is also above average (~51%).
  - **Blue‑collar**, **entrepreneur**, **services**, and **housemaid** roles show lower conversion rates (around 36–40%).

- **Contact method**
  - Most contacts are made via **cellular** (over 8,000 records), with far fewer via **telephone** and some with **unknown** contact type.
  - Conversion is highest for **cellular** (~54%), slightly lower for **telephone** (~50%), and much lower for the **unknown** contact type (~23%).
  - This suggests **cellular** is the most effective and most used channel.

- **Marital status**
  - The majority of clients are **married**, followed by **single** and **divorced** customers.
  - **Single** customers have the highest conversion rate (~54%), followed by **divorced** (~48%), while **married** customers convert at a lower rate (~44%).

- **Education level**
  - Most customers have **secondary** education (~5,500), followed by **tertiary**, then **primary**; the **unknown** category is small.
  - Conversion is highest among customers with **tertiary** education (~54%), followed by **unknown** (~51%) and **secondary** (~45%).  
    **Primary** education has the lowest conversion (~39%).

- **Previous campaign outcome (`poutcome`)**
  - Most customers have an **unknown** previous outcome (over 8,000 records); only a minority have recorded **success**, **failure**, or **other** results.
  - Customers with a **previous success** have a very high current conversion rate (around **90%**), much higher than those with failure, other, or unknown outcomes.
  - This indicates that **retargeting customers who previously responded positively is extremely effective**.

---

## Business Recommendations

Based on the EDA:

- **Prioritize high‑response segments** such as:
  - Students, retired, unemployed, and management roles.
  - Customers with tertiary education.
  - Single clients (marital status).

- **Focus on effective channels**
  - Continue prioritizing **cellular** contacts, as they reach the most customers and achieve the highest conversion rates.
  - Review records with **unknown** contact type and improve data quality.

- **Leverage previous campaign history**
  - Build targeted campaigns specifically for customers with a **previous successful** outcome, as they are far more likely to subscribe again.
  - Design re‑engagement strategies for customers with previous failures but avoid over‑contacting low‑probability segments.

---

## Repository Structure

```text
.
├── bank_marketing_eda.ipynb   # Main Jupyter notebook with full analysis
├── data/
│   └── bank.csv               # (Optional) Raw dataset or link in README
└── README.md                  # Project description (this file)
