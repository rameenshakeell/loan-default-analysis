# Loan Default Analysis – Lending Club Case

This project is a two-part analysis of loan default behavior using publicly available Lending Club data. The goal was to explore patterns, identify risk indicators, and prepare features for predictive modeling that could help determine whether a loan would be fully paid or charged off.

## 📂 Project Structure

- `loan-default-analysis-part1.Rmd`: Exploratory data analysis (EDA) and risk profiling by loan grade, subgrade, amount, and borrower attributes.
- `loan-default-analysis-part2.Rmd`: Feature engineering and modeling setup for loan default prediction.

## 🧠 Project Objectives

- Understand how loan status varies by grade, subgrade, and borrower characteristics
- Analyze the distribution of loan amounts and interest rates
- Examine the relationship between FICO scores, employment length, and loan outcome
- Prepare variables for classification modeling
- Clean and transform categorical and numerical features

## 📊 Key Tasks Performed

### Part 1: Exploratory Data Analysis
- Proportion of charged-off vs fully paid loans
- Analysis by loan grade and subgrade
- Visual comparisons of loan amount across risk categories
- Relationship between borrower FICO score and loan status
- Use of `ggplot2` for multi-dimensional visualizations

### Part 2: Feature Engineering & Modeling
- Binned and transformed FICO scores, income, and employment data
- Created dummy variables for categorical features
- Engineered a target variable suitable for classification
- Set up training/test dataset structure

> *Note: While this project focuses on analysis and preparation, model training was intentionally left for a future phase.*

## 🛠️ Tools & Libraries

- R
- tidyverse (`dplyr`, `ggplot2`, `readr`, `stringr`)
- lubridate
- base R functions for transformation & visualization

## 📌 Skills Demonstrated

- Data wrangling & transformation
- Exploratory data analysis (EDA)
- Risk profiling
- Feature engineering for classification models
- Data visualization and insight generation

## 👤 Author

Rameen Shakeel  
MS in Business Analytics, University of Illinois Chicago  
[LinkedIn](https://www.linkedin.com/in/rameenshakeel)

