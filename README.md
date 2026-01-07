# Bank Marketing Campaign – EDA and Subscription Prediction

## Overview

This project analyzes a bank marketing dataset to understand **which customers are most likely to subscribe to a term deposit** and to build machine learning models that predict subscription.

The work is split into two main parts:

1. **Exploratory Data Analysis (EDA)** – understand the data, customer segments, and campaign performance.
2. **Modeling** – build and compare classification models (Logistic Regression and Random Forest) to predict whether a customer will subscribe.

This project was done as part of my data science learning path after completing the IBM Data Science Professional Certificate.

---

## Dataset

- **Source:** Bank Marketing dataset from a Portuguese bank (available on Kaggle / UCI Machine Learning Repository).
- **Rows:** 11,162 customers  
- **Columns:** 17 original features + engineered features for analysis/modeling.

### Target variable

- `deposit` – whether the client subscribed to a term deposit:
  - `"yes"` – subscribed
  - `"no"` – did not subscribe

For modeling, I created a numeric target:

- `deposit_flag`:
  - `1` if `deposit == "yes"`
  - `0` otherwise

The class distribution is slightly imbalanced:

- ~47% subscribed (`deposit_flag = 1`)
- ~53% did not subscribe (`deposit_flag = 0`)

### Main features

- **Client profile:**  
  `age`, `job`, `marital`, `education`, `default`, `balance`, `housing`, `loan`
- **Campaign contact information:**  
  `contact` (cellular / telephone), `day`, `month`, `duration`, `campaign`
- **Previous campaign results:**  
  `pdays`, `previous`, `poutcome` (outcome of prior contacts)

Engineered features:

- `age_group` – age binned into `<30`, `30–40`, `40–50`, `50+`
- `deposit_flag` – binary target for modeling

---

## Objectives

1. **EDA**
   - Understand the overall performance of the marketing campaign.
   - Identify **which customer segments** (age, job, education, marital status) respond best.
   - Compare the effectiveness of **different contact methods**.
   - Analyze the impact of **previous campaign outcomes**.

2. **Modeling**
   - Build and evaluate a **baseline** Logistic Regression model.
   - Build and evaluate a **Random Forest** model using the same features.
   - Compare the models and recommend the one that best supports the business goal:
     - **Identify as many potential subscribers as possible** while keeping wasted calls reasonable.

