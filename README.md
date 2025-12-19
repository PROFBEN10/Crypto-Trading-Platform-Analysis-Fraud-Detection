# Crypto-Trading-Platform-Analysis-Fraud-Detection
Analyzed crypto trading and user activity data, engineered behavioral features, build a fraud detection model and deliver data-driven market and security recommendation.s


### Case Study Overview

This project analyzes trading and user activity data from a crypto trading platform to uncover market insights, understand user behavior, and build a machine learning model to detect potentially fraudulent users.

The goal is not only to build models, but to demonstrate clear reasoning, clean data analysis, and actionable business insights—with a strong focus on real-world decision-making.

#### Problem Statement

The platform faces two key challenges:

Understanding user and market behavior

Which trading pairs drive the most volume?

When are users most active?

How volatile are key markets?

Improving platform security

Identify users who deposit funds, trade minimally, and quickly withdraw—a common fraudulent pattern.

Build a scalable and explainable fraud detection model.

Additionally, the analysis supports a hypothetical business decision:

Launching a Low-Volume Trader marketing campaign in Kenya.

#### Datasets Used

Two datasets were provided:

###### trades.csv

Contains executed trades on the platform.

timestamp – Trade time

user_id – Unique user identifier

pair – Trading pair (e.g., BTCNGN, BTCUSDT)

side – Buy or Sell

volume – Amount of base asset traded

amount – Total value of the trade in quote currency

###### user_activity.csv

Captures deposits and withdrawals.

timestamp – Activity time

user_id – Unique user identifier

activity_type – Deposit or Withdrawal

asset – Asset involved

amount – Amount deposited or withdrawn

#### Data Preparation

All timestamps were standardized to datetime format.

Trade amounts were normalized to USD for consistent comparison.

User activity amounts were handled using asset-normalized features due to missing unit prices.

Data was aggregated to the user level for modeling.

### Exploratory Data Analysis (EDA)

#### Market Dynamics

Trading volume was aggregated by pair to identify liquidity concentration.

BTC-related pairs dominate total trading volume, highlighting Bitcoin’s central role on the platform.

Stablecoin pairs act as key entry points for users.

#### Volatility Analysis (BTCNGN)

Daily price volatility was calculated using standard deviation.

A 7-day rolling average was applied to smooth short-term noise.

Insight:
Volatility fluctuates in cycles, and rolling averages provide a clearer view of market risk trends.

#### User Deposit Behavior

Deposits peak on Fridays, Saturdays and Wednesday, significantly weekends.

Higher activity occurs during regular business hours especially 12pm.

#### Business Implication:
Marketing campaigns and system scaling can be aligned with peak activity periods.

### Fraud Detection (Machine Learning)

#### Feature Engineering

User-level features were engineered from both datasets, including:

Deposit and withdrawal counts and totals

Time between first deposit and first withdrawal

Total trade volume and trade frequency

Trade-to-deposit and withdrawal-to-deposit ratios

Number of unique assets traded

These features capture behavioral intent, not just transaction size.

#### Target Labeling

Since no fraud label existed, a rule-based heuristic was used to define a is_suspicious flag.
Users were labeled suspicious if they:

Deposited funds,

Made minimal trades,

Withdrew funds shortly after depositing.

This mirrors real-world fraud detection heuristics.

#### Models Built

##### Logistic Regression (Baseline)

Simple and interpretable

Struggled with non-linear patterns

Missed several suspicious users

##### Random Forest Classifier (Final Model)

Captured complex behavioral interactions

Achieved high precision and recall

Very few false positives and strong fraud detection capability

Why Random Forest?

Handles non-linear relationships well

Robust to noisy data and outliers

Ideal for behavior-based fraud detection

#### Model Performance (Random Forest)

High Precision: Most flagged users were truly suspicious

High Recall: Majority of fraud cases were successfully detected

Balanced performance suitable for production environments

### Strategic Recommendation

Low-Volume Trader Campaign – Kenya

Using behavioral insights from the data, the target audience is defined as:

Low-Volume Traders who:

Have low cumulative trading volume (USD)

Trade infrequently

Show low trade-to-deposit ratios

#### Additional Filters:

Users active in Kenya-related currency pairs

Exclusion of users flagged as suspicious

#### Business Value

This segment represents users with clear intent but low engagement.
Targeted incentives such as:

Reduced fees

Educational content

Beginner-friendly tools

can convert these users into more active traders without increasing platform risk.

### Tools & Technologies

Python

Pandas & NumPy – Data manipulation

Matplotlib & Seaborn – Visualization

Scikit-learn – Machine learning models

Jupyter Notebook – Analysis and documentation


#### Conclusion

This project demonstrates how data analysis, machine learning, and business thinking come together to solve real-world problems. The approach balances technical rigor with practical insights, making it suitable for both security and growth-focused decision-making.
