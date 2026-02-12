# Loan Default Prediction & Investment Strategy Analysis  
**Lending Club Case Study**

This project analyzes loan default risk and investment performance using historical data from Lending Club, a peer-to-peer (P2P) lending platform. The objective is to support **data-driven investment decisions** by identifying loans that balance default risk and expected returns.

Rather than focusing solely on prediction accuracy, this analysis emphasizes **decision analytics** , evaluating how different modeling approaches translate into real investment outcomes under risk.

---

## Problem Context

Online lending platforms enable investors to fund personal loans with varying risk–return profiles. While higher-risk loans offer higher interest rates, defaults can significantly erode returns. Effective investment strategies therefore require:

- Identifying loans likely to be fully repaid  
- Estimating expected returns and losses  
- Translating model predictions into actionable portfolio decisions  

This project addresses these challenges using historical loan performance data.

---

## Objectives

1. **Predict loan default risk** (Fully Paid vs. Charged Off) using borrower and loan attributes available *before loan issuance*  
2. **Model loan returns** as a continuous outcome to capture profitability beyond default classification  
3. **Evaluate models from an investment perspective**, incorporating profit, loss, and opportunity cost  
4. **Design and compare investment strategies** based on model outputs  

---

## Data Overview

- Source: Lending Club loan data (2013–2015)  
- Scope: 36-month loans with completed outcomes  
- Target variables:
  - `loan_status` (classification: Fully Paid / Charged Off)
  - `actualReturn` (regression: net dollar return per loan)

Only variables available at the time of loan funding were retained to prevent **data leakage**.

---

## Methodology

### 1. Exploratory Data Analysis (EDA)
- Analyzed default rates across loan **grades and sub-grades**
- Examined relationships between:
  - Interest rates and default
  - Loan amounts and grades
  - Borrower FICO scores, income, and employment length
- Evaluated loan purposes and their association with risk and performance
- Computed **actual loan term** and **annualized returns**

Key insight: Loan grade and sub-grade provide strong but imperfect signals of risk, highlighting the need for additional borrower-level features.

---

### 2. Feature Engineering
Constructed economically meaningful derived variables, including:
- **Adjusted Debt-to-Income Ratio**  
- **Payment-to-Income Ratio**
- **Credit Utilization Metric**

These features better captured borrower financial strain than raw variables alone.

---

### 3. Missing Data & Leakage Control
- Variables with excessive missingness (>60%) were excluded
- Context-aware imputation was applied where appropriate
- Post-issuance variables (e.g., payment history, recoveries, hardship flags) were removed to avoid hindsight bias

This ensured models reflected **real-world deployment constraints**.

---

### 4. Univariate Screening
- Used **AUC** to assess individual predictor strength for a binary outcome
- Identified informative predictors while flagging variables with suspiciously high performance as potential leakage

---

### 5. Predictive Modeling

#### Loan Status (Classification)
- Decision Tree (rpart)
- Random Forest
- Gradient Boosted Trees (XGBoost)

Models were evaluated using:
- Confusion matrices
- ROC curves and AUC
- Lift analysis

While simple trees performed poorly, ensemble models captured nonlinear interactions more effectively.

---

#### Loan Returns (Regression)
- Lasso-regularized GLM
- Random Forest regression
- Gradient Boosted Trees (XGBoost)

Performance was evaluated using **RMSE**, prioritizing control of large monetary errors.

---

## Investment Strategy Evaluation

Model outputs were translated into **investment decisions**, not just predictions:

- Compared expected profits against a **risk-free benchmark (bank CDs)**
- Evaluated classification thresholds based on profitability
- Ranked loans by predicted probability of repayment and predicted returns
- Designed a **combined expected-return metric**:
  expected_return = P(Fully Paid) × Predicted Return

  This combined strategy outperformed approaches based solely on default risk or returns.

---

## Advanced Analysis: Lower-Grade Loan Strategy

To explore higher-yield opportunities, models were retrained on **lower-grade loans (C and below)**.  
Random Forest models achieved the strongest performance, indicating that selective investment in riskier segments can outperform conservative strategies when guided by robust analytics.

---

## Key Insights

- Default prediction alone is insufficient for optimal investment decisions  
- Combining **risk and return modeling** leads to superior outcomes  
- Ensemble models outperform simple classifiers in capturing borrower risk dynamics  
- Thoughtful feature engineering and leakage control are critical for credible results  

---

## Tools & Technologies

- **R**
- tidyverse (dplyr, ggplot2)
- ranger (Random Forest)
- rpart (Decision Trees)
- xgboost
- glmnet (Lasso Regression)
- ROCR (model evaluation)

---

## Project Structure

- `loan-default-analysis-part1.Rmd` — EDA, risk profiling, feature engineering  
- `loan-default-analysis-part2.Rmd` — Modeling, evaluation, and investment strategies  

---

## Notes

This project demonstrates an end-to-end **decision analytics workflow**, from exploratory risk analysis to model-driven investment strategy design, with a focus on interpretability, realism, and business relevance.

## How to Run (Reproducibility)

This repository does not include the original dataset used in the analysis (it was provided for academic use as part of IDS 572).

To reproduce the workflow, you have two options:

**Option A — Use a comparable public Lending Club dataset**
1. Download a public Lending Club loan dataset (e.g., 2013–2015 loans) from a reputable source.
2. Save the file locally as `data/loans.csv`.
3. Open `loan-default-analysis_partB_modeling.Rmd` in RStudio.
4. Update the data import line to point to your local file path (and adjust column names if needed).
5. Install required packages and run the notebook top-to-bottom.

**Option B — Review as a case study**
If you do not have access to the dataset, the README and notebook still document:
- the decision task (default + returns modeling),
- methodology,
- feature engineering,
- evaluation approach,
- and investment strategy logic.

