# 🏨 Customer Segmentation with RFM Model & K-Means Clustering
### Case Study: Hospitality Business

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

---

## 📌 Overview

This project applies **RFM (Recency, Frequency, Monetary)** analysis combined with **K-Means Clustering** to segment customers of a hospitality business

The goal is to turn raw transaction data into actionable customer segments that can inform targeted marketing strategies, loyalty programs, and re-engagement campaigns.

---

## 🧩 Problem Statement

The business had no data-driven understanding of their customer types. Without segmentation:
- Marketing efforts were not targeted
- Loyal customers weren't being rewarded
- Inactive customers weren't being re-engaged
- Resources were allocated inefficiently

---

## 🗂️ Dataset

| Attribute | Details |
|-----------|---------|
| Source | Booking records |
| Period | February, 2024 – May, 2024 |
| Records | 183 unique customers |

---

## ⚙️ Methodology

```
Raw Transaction Data
        ↓
  Data Selection          → Build RFM fields from booking records
        ↓
  Data Cleansing          → Handle nulls & duplicates
        ↓
  Elbow Method            → Determine optimal k
        ↓
  K-Means Clustering      → Segment customers into k groups
        ↓
  Silhouette Evaluation   → Validate cluster quality
        ↓
  Cluster Analysis        → Interpret and label each segment
```

### RFM Dimensions

| Metric | Description | Higher Score = |
|--------|-------------|----------------|
| **R** — Recency | Days since last transaction | More recently active |
| **F** — Frequency | Number of transactions | More loyal / frequent |
| **M** — Monetary | Total spending amount | Higher revenue contribution |

### Finding Optimal K

The **Elbow Method** was used to determine the optimal number of clusters. The distortion score plot showed a clear elbow at **k = 3** (distortion score = 198.505).

### Cluster Validation

| Metric | Value | Interpretation |
|--------|-------|----------------|
| Silhouette Coefficient | **0.521** | Good cluster separation |

---

## 📊 Results

Three customer segments were identified:

| Segment | Cluster | Customers | Recency | Frequency | Monetary |
|---------|---------|-----------|---------|-----------|----------|
| 🟢 **Loyal / Active** | Cluster 1 | 20 (11%) | 0.426 | 0.300 | 0.376 |
| 🔵 **New Customers** | Cluster 2 | 106 (58%) | 0.424 | 0.022 | 0.005 |
| 🔴 **Inactive** | Cluster 0 | 57 (31%) | 0.860 | 0.025 | 0.007 |

> R, F, M values are normalized (0–1). Lower R = more recent. Higher F & M = more engaged.

---

## 📣 Recommended Strategies

### 🟢 Loyal / Active Customers (Cluster 1)
- Implement advanced loyalty program with VIP tiers
- Offer exclusive deals and early access to new services
- Use cross-sell & up-sell strategies with premium room upgrades
- Invite them to provide feedback and participate in service development

### 🔵 New Customers (Cluster 2)
- Send welcome emails with first-time booking discounts
- Introduce the loyalty program early to drive retention
- Offer time-limited promotions to incentivize repeat bookings
- Personalize the onboarding experience

### 🔴 Inactive Customers (Cluster 0)
- Launch re-engagement campaigns via email, SMS, or social media
- Offer exclusive win-back discounts
- Send satisfaction surveys to understand reasons for inactivity
- Highlight new facilities or services added since their last visit

---

## 🛠️ Tech Stack

| Category | Tools |
|----------|-------|
| Language | Python 3.x |
| Data Processing | Pandas, NumPy |
| Machine Learning | Scikit-learn, RapidMiner |
| Visualization | Matplotlib, Seaborn, Yellowbrick |
| Notebook | Google Colab |

---

## 📈 Key Insights

- **58% of customers** are new with low engagement — a major opportunity for conversion
- **Only 11%** are truly loyal, yet they generate the highest revenue per customer
- **31% are inactive** — a potential re-engagement pool worth targeting with the right campaigns
- A Silhouette score of **0.521** confirms well-separated, meaningful clusters

---

## 🔮 Future Improvements

- [ ] Add customer satisfaction scores as an additional RFM dimension
- [ ] Build a real-time segmentation pipeline
- [ ] Compare results with other clustering algorithms (DBSCAN, Hierarchical Clustering)
- [ ] Develop an interactive dashboard for business users

---

## 👤 Author

**Farhan Fadhilah Rasyid**
- GitHub: [@farhanfdlh](https://github.com/farhanfdlh)

---
