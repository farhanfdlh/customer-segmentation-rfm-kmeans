# Hospitality Customer Segmentation — RFM & K-Means Clustering

> Segmenting 183 hotel customers using RFM (Recency, Frequency, Monetary) analysis and K-Means clustering, turning raw booking transactions into actionable customer segments for targeted marketing and retention.

---

## 📑 Table of Contents

- [Business Background](#-business-background)
- [Business Objective](#-business-objective)
- [Data Overview](#-data-overview)
- [Approach and Methodology](#-approach-and-methodology)
- [Key Findings](#-key-findings)
- [Business Impact and Recommendations](#-business-impact-and-recommendations)
- [Future Improvements](#-future-improvements)
- [Tools & Tech Stack](#%EF%B8%8F-tools--tech-stack)
- [Repository Structure](#-repository-structure)
- [Author](#-author)

---

## 📌 Business Background

The business had no data-driven understanding of who its customers actually were. Every customer was treated the same in marketing and retention efforts — meaning loyal, high-value guests weren't being specifically rewarded, inactive guests weren't being re-engaged, and marketing budget was spread evenly instead of being directed where it would have the most impact.

## 🎯 Business Objective

Turn raw booking transaction data into **actionable customer segments** by:
- Quantifying each customer's engagement using RFM (Recency, Frequency, Monetary) metrics
- Grouping customers into meaningful segments using K-Means clustering
- Translating each segment into a concrete marketing/retention strategy the business can act on

## 📂 Data Overview

| Attribute | Details |
|---|---|
| Source | Hotel booking records |
| Period | February 2024 – May 2024 (110 days) |
| Customers | 183 unique customers |
| Raw fields | Customer ID, check-in/check-out dates, room type, stay type, price |

**RFM Dimensions**

| Metric | Description | Higher Score Means |
|---|---|---|
| **R** — Recency | Days since last transaction | More recently active |
| **F** — Frequency | Number of transactions | More loyal / frequent |
| **M** — Monetary | Total spending amount | Higher revenue contribution |

## 🔧 Approach and Methodology

Raw booking records don't carry RFM values directly — each customer's transactions had to be aggregated into a single RFM row: **Recency** as days since their last booking, **Frequency** as their total number of bookings, and **Monetary** as their total spend across all bookings in the period. This aggregation was done directly in **Excel**. Duplicates and null values were checked for at this stage (none were found in the final dataset).

```
Raw Transaction Data (booking records)
        ↓
Data Selection & RFM Construction   → Aggregate bookings into Recency, Frequency, Monetary (Excel)
        ↓
Elbow Method + Silhouette Check      → Determine and validate optimal k (Python notebook)
        ↓
K-Means Clustering                   → Run final clustering with validated k = 3 (RapidMiner / Altair AI Studio)
        ↓
Cluster Analysis                     → Interpret and label each segment
```

The optimal number of clusters was first determined and validated in Python: the **Elbow Method** pointed to **k = 3** (distortion score = 198.505), confirmed by a **Silhouette Coefficient of 0.521** (good separation). That validated k was then configured in RapidMiner to run the actual clustering process and produce the final segment assignments used in the results below.

## 🔍 Key Findings

Three distinct customer segments emerged from the clustering:

| Segment | Customers | Recency | Frequency | Monetary | Profile |
|---|---|---|---|---|---|
| 🟢 **Loyal / Active** | 20 (11%) | 0.426 | 0.300 | 0.376 | Recently active, frequent, high spend |
| 🔵 **New Customers** | 106 (58%) | 0.424 | 0.022 | 0.005 | Recently active, but low engagement so far |
| 🔴 **Inactive** | 57 (31%) | 0.860 | 0.025 | 0.007 | Long since last transaction, minimal engagement |

*(R, F, M values normalized 0–1; lower Recency = more recent, higher Frequency/Monetary = more engaged.)*

- **58% of the customer base is new**, with low engagement so far — the largest untapped opportunity for conversion into repeat guests
- **Only 11% are truly loyal**, yet this small group generates the highest revenue per customer — disproportionately valuable relative to its size
- **31% of customers are inactive**, representing a meaningful re-engagement pool rather than a lost cause

## 💡 Business Impact and Recommendations

**🟢 Loyal / Active Customers (11%) — Protect and grow this segment**
- Introduce a tiered loyalty program with VIP benefits to reduce the risk of losing the business's most valuable guests to competitors
- Offer premium room upgrades and cross-sell relevant add-on services
- Involve them directly in feedback loops — this group's input is the highest-signal source for service improvement

**🔵 New Customers (58%) — Convert engagement into loyalty**
- Send first-time booking discounts and welcome offers shortly after their first stay, while intent is still fresh
- Introduce the loyalty program early, since this segment is the largest lever for future revenue growth
- Personalize onboarding communication instead of generic mass marketing

**🔴 Inactive Customers (31%) — Win back or confirm the loss**
- Run targeted win-back campaigns with exclusive discounts
- Use satisfaction surveys to understand *why* they stopped booking, rather than guessing
- Highlight new facilities or service changes since their last visit, in case their disengagement was situational rather than dissatisfaction-driven

**Overall business case**: instead of spreading a flat marketing budget evenly across all 183 customers, the business can now allocate spend proportionally to segment value — protect the 11% driving disproportionate revenue, convert the 58% still on the fence, and selectively win back the 31% at risk of being fully lost.

## 🔮 Future Improvements

- Add customer satisfaction scores as an additional dimension beyond RFM
- Build a real-time or periodically refreshed segmentation pipeline instead of a one-time snapshot
- Compare results against other clustering algorithms (DBSCAN, Hierarchical Clustering) to validate segment stability
- Develop an interactive dashboard so business users can explore segments without needing to re-run the analysis

## 🛠️ Tools & Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.x |
| Data Processing | Excel, Pandas, NumPy |
| Machine Learning | Scikit-learn, RapidMiner |
| Visualization | Matplotlib, Seaborn, Yellowbrick |
| Notebook | Google Colab |

## 📂 Repository Structure

```
customer-segmentation-project/
├── hospitality_customer_segmentation.ipynb        # Elbow Method + Silhouette Coefficient — determines optimal k
├── hospitality_customer_segmentation.pdf          # One-page project summary report
├── k-means-customer-segmentation.rmp              # RapidMiner (Altair AI Studio) process — runs final K-Means clustering
└── README.md
```

*(RFM construction from raw booking records was done in Excel and isn't included as a code file.)*

## 👤 Author

**Farhan Fadhilah Rasyid**

[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/farhanfdlh)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/farhan-fadhilah-rasyid)
[![Website](https://img.shields.io/badge/Website-000000?style=for-the-badge&logo=google-chrome&logoColor=white)](https://farhan-portfolio-smoky.vercel.app)
