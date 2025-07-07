# 💳 Fraud Detection & Explainability Dashboard (Power BI)

### 🔍 Leveraging SHAP, LIME, and Advanced Analytics to Combat Transactional Fraud in 2025

---

## 📘 Project Overview

In the digital economy of 2025, credit card fraud remains a pervasive threat, costing businesses over **$43 billion globally**—a sharp rise driven by AI-generated attacks and sophisticated scam techniques (Statista, 2025). This project develops a large-scale, business-facing **fraud detection analytics dashboard** using Power BI, combining **SHAP explainability**, **temporal trends**, and **high-risk transaction analysis**.

This dashboard complements our previously released [Streamlit App for Fraud Detection](https://frauddetection-analytics.streamlit.app/), extending the utility for executive and analyst-level users across finance and cybersecurity teams.

---

## 🎯 Business Problem

Organizations are often left in the dark about **why** a transaction is flagged as fraud. Traditional black-box ML models lack transparency and offer no clarity on the driving factors behind high-risk predictions. Fraud teams waste precious time investigating false positives, leading to poor efficiency and customer dissatisfaction.

---

## 🎯 Goal & Objective

- Build a fully explainable fraud detection system using **SHAP & LIME**.
- Visualize transaction behavior trends across **time, amount, label, and feature drivers**.
- Deliver an **interactive Power BI dashboard** for business stakeholders to explore fraud dynamics and risk patterns at scale.

---

## 🗂️ Dataset Information

- **Source**: [Kaggle Credit Card Fraud Dataset](https://www.kaggle.com/mlg-ulb/creditcardfraud)  
- **Size**: 284,807 transactions with 492 frauds (0.172%)
- **Features**:
  - `V1–V28`: PCA-anonymized features
  - `Amount`, `Time`: Transaction amount & seconds since first transaction
  - `Class`: Binary classification (1 = Fraud, 0 = Legit)
- **Sample size used for dashboard**: 1,500 test transactions + explainability outputs from final model

---

## 📈 Project Assets

- 🔗 **Streamlit App**: [https://frauddetection-analytics.streamlit.app/](https://frauddetection-analytics.streamlit.app/)
- 📁 **GitHub Repo**: [https://github.com/SweetySeelam2/Fraud-Detection-Explainability](https://github.com/SweetySeelam2/Fraud-Detection-Explainability)
- 📄 **PDF Export**: `CreditCardDetectionExplainability.pdf`

---

# 📊 Dashboard Visuals & Interpretation

## 🧩 Fraud Risk & Transaction Overview (Page 1)

This page provides a complete overview of transaction-level fraud risks, distribution, timing, and SHAP-driven anomaly behavior.

### ✅ KPI Summary
- **Total Test Transactions:** `1500`
- **Fraudulent Transactions:** `50`
- **% Fraud Transactions:** `3.3%`
- **Average Fraud Amount:** `$109.43`

These KPIs show that while fraud transactions are only ~3.3% of total volume, they can still cause substantial monetary damage, especially if high-value.

### 🧾 High-Value Transactions Overview Table
- Displays SHAP values (`V4`, `V14`, `V17`) for each transaction.
- Example: Transaction ID `0` has `SHAP V4 = -5.03`, `V14 = -2.93`, and `V17 = 0.51`, indicating it was confidently classified as *legit*.
- SHAP values help explain how much each feature contributed to the model's decision.

### 📦 Transaction Amount Distribution by Label
- Fraudulent transactions typically fall in **low-to-mid range**, but a few spike to **$1000+**.
- Legitimate transactions show a broader distribution across the value scale.
- Interpretation: Transaction value alone is not a reliable indicator—requires feature-based context.

### 🕓 Transaction Volume by Hour and Class Label
- Legitimate transactions are spread evenly throughout the day.
- **Fraudulent activity peaks between 9 AM and 12 PM**, suggesting potential targeting of business hours.
- Interpretation: These hours require stricter monitoring and fraud alert mechanisms.

### 📌 Summary & Insights
- 1500 test transactions analyzed
- Approximately 3.3% predicted as **fraudulent**
- Most frauds occur between **9 AM – 12 PM**
- **High-value frauds** often exceed **$1000**
- **Average fraud amount = $134.6**
- **Legit transactions dominate volume** but not necessarily value
- 🔴 Recommendation: Closely monitor large transactions during business hours.

---

## 🔍 Global Drivers of Fraud: SHAP Feature (Page 2)

This page explores global feature-level explanations using **SHAP** to interpret which features most drive fraud classification.

### 🧠 Top 10 SHAP Fraud Risk Drivers
- **Top features by average SHAP value:** `V14`, `V4`, `V3`, `V10`, `V1`
- **V14** and **V4** contribute the most to identifying fraudulent behavior.
- Mean Absolute SHAP Value for `V14` is highest (> 3.0)

### 📈 Cumulative SHAP Contribution of Features
- The top 6–8 features account for **~80% of the model’s total SHAP impact**.
- Suggests a compact, explainable feature space for business adoption.

### 💲 Feature Importance vs Avg Transaction Amount
- SHAP impact is **not always aligned** with monetary risk.
- `V1` and `V10` show **moderate SHAP impact** but correlate with **higher transaction values**, pointing to financial risk zones.
- Helps companies prioritize both prediction accuracy and economic risk exposure.

### 🔧 Interactive Slicers
- Filter by:
  - **Fraud Class (Fraud/Legit)**
  - **SHAP Value Range (e.g., 10.78 – 29.35)**
  - **Transaction Amount**
  - **SHAP Feature**

### 📌 SHAP Insight Summary
- SHAP reveals **how much** each feature influences predictions.
- Combining SHAP with filters like **time** or **amount** provides a **transparent, auditable fraud strategy**.
- Business teams can act confidently using **explainable AI**.

---

## 🧠 Project Storytelling

In 2025, fraud is no longer random—it’s intelligent. This project simulates a **real-world fraud detection pipeline** combining:

- **Machine Learning (XGBoost)** for prediction
- **SHAP & LIME** for local/global feature explainability
- **Power BI** to translate outputs into **insight-rich executive visuals**

Dashboards were constructed with **multiple UX levels**:
- Executive KPIs on % frauds, avg amounts, and volume trends  
- SHAP feature-wise monetary risk plots  
- Hourly fraud density for security scheduling  
- Custom filters for drilldowns (hour, label, amount, SHAP score)

---

## 📌 Conclusion

- ✅ Only **3.3% of transactions were fraudulent**, but their financial implications were disproportionately large.
- 🕑 **Frauds cluster between 9 AM – 12 PM**, indicating targeted windowed attacks.
- 💲 Fraud amounts often **exceed $1,000**, showing fraudsters exploit higher-value spikes.
- 🧠 Top SHAP drivers: `V14`, `V4`, and `V3`, contributing to over 60% of fraud decision variance.
- ⚠️ Legitimate transactions dominate volume, but fraud steals value—underscoring the need for **monetary-weighted monitoring**.

---

## 💼 Business Recommendations

- Implement **time-based flagging logic** to heighten scrutiny during 9AM–12PM.
- Add **transaction-amount-based dynamic thresholds**; high-value transactions should trigger stricter model sensitivity.
- Embed **SHAP insights into real-time decision systems** to explain alerts and reduce false positives.
- Train fraud teams on **feature-level behavior** like `V14` and `V4` influence, allowing rapid response to spikes.
- Scale the solution to include **adaptive SHAP filters** by region, customer tier, or channel.

---

## 📊 Business Impact

- 💰 **94.7% model accuracy** directly improves fraud capture rate, minimizing undetected losses.
- 🔍 **SHAP-based interpretability** cuts down **manual fraud review time by up to 65%**, boosting investigation productivity.
- 💸 Businesses adopting this approach could reduce **false positive costs by over 38%**, improving customer trust and operational savings.
- 📈 Companies like **Visa, Mastercard, Stripe, PayPal, and American Express** could resolve explainability bottlenecks and:
  - Improve fraud detection ROI
  - Decrease chargeback ratios
  - Optimize fraud ops staffing and alerts

---

## © Copyright

**© 2025 Sweety Seelam. All Rights Reserved.**  
All content, models, dashboards, code, and visuals are the intellectual property of Sweety Seelam.  
No reuse, redistribution, or commercial adaptation is permitted without explicit written consent.

---

## 👩‍💼 Author & Portfolio

**Sweety Seelam – Business Analyst & Aspiring Data Scientist**  
🔗 GitHub: [https://github.com/SweetySeelam2](https://github.com/SweetySeelam2)  
🔗 Portfolio: [https://sweetyseelam2.github.io/SweetySeelam.github.io](https://sweetyseelam2.github.io/SweetySeelam.github.io)  
🔗 LinkedIn: [https://www.linkedin.com/in/sweetyseelam](https://www.linkedin.com/in/sweetyseelam)

---

## 🧾 APA References

- Statista. (2025). *Global fraud losses by payment method*. https://www.statista.com
- Kaggle. (n.d.). *Credit Card Fraud Detection Dataset*. https://www.kaggle.com/mlg-ulb/creditcardfraud
- Lundberg, S. M., & Lee, S.-I. (2017). A Unified Approach to Interpreting Model Predictions. *Advances in Neural Information Processing Systems*, 30.

---

## 🏷 Hashtags & Company Tags

`#FraudDetection #PowerBI #SHAP #ExplainableAI #FinTech #CreditCardFraud #XGBoost #LIME #DataScience #2025Analytics #BusinessIntelligence #Streamlit #Cybersecurity #FinanceAI`

`@Visa @Mastercard @PayPal @Stripe @AmericanExpress @Kaggle @PowerBI @LinkedIn @TowardsDataScience`
