# 📊 End-to-End Sales Analytics Pipeline

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![SQL](https://img.shields.io/badge/SQL-SQL%20Server-CC2927?logo=microsoftsqlserver)
![PowerBI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi)
![Excel](https://img.shields.io/badge/Excel-Data%20Prep-217346?logo=microsoftexcel)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📌 Project Overview

A full analytics pipeline — from **raw data** all the way to a **stakeholder-ready dashboard** — simulating how real business intelligence teams work.

**Business Question:** Which products and regions are driving revenue, which are underperforming, and what does the sales trend look like over time?

---

## 🏗️ Pipeline
```
Raw CSV → [Excel] inspect → [Python] clean & EDA → [SQL] query & analyse → [Power BI] dashboard
```

---

## 📊 Dataset

| Property | Detail |
|---|---|
| Source | Retail sales dataset |
| Records | 50,000+ transactions |
| Columns | Order ID, Product, Category, Region, Sales, Profit, Date |
| Period | 3 years of transaction history |

---

## 🔧 Tech Stack

- **Python / Pandas** — data cleaning & EDA
- **SQL Server / SSMS** — business logic & aggregation
- **Power BI** — interactive dashboard
- **Microsoft Excel** — initial data profiling

---

## 🧹 Data Cleaning (Python)

- Removed 340 duplicate order records
- Handled 1,200+ missing values (filled with category median)
- Standardized inconsistent date formats
- Flagged negative profit rows for review

---

## 🔍 SQL Highlights
```sql
-- Product revenue ranking
SELECT TOP 10
    Product,
    SUM(Sales) AS Total_Revenue,
    RANK() OVER (ORDER BY SUM(Sales) DESC) AS Revenue_Rank
FROM sales_cleaned
GROUP BY Product
ORDER BY Total_Revenue DESC;

-- Month-over-month growth
WITH monthly AS (
    SELECT FORMAT(Order_Date, 'yyyy-MM') AS Month, SUM(Sales) AS Monthly_Sales
    FROM sales_cleaned GROUP BY FORMAT(Order_Date, 'yyyy-MM')
)
SELECT Month, Monthly_Sales,
    ROUND((Monthly_Sales - LAG(Monthly_Sales) OVER (ORDER BY Month)) /
          LAG(Monthly_Sales) OVER (ORDER BY Month) * 100, 2) AS MoM_Growth_Pct
FROM monthly;
```

---

## 📈 Key Findings

- Top 3 products drove **58% of total revenue**
- 2 regions performed **30%+ below the sales average**
- Q4 consistently outperformed Q1 by **~22%**
- Profit margins ranged from **4% to 38%** across categories

---

## 🚀 How to Run
```bash
git clone https://github.com/harshavardhanchittapragada-max/sales-data-analysis.git
cd sales-data-analysis
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook
```

---

## 💡 What I Learned

- Real pipelines have multiple stages — no single tool does everything
- SQL window functions are far more powerful than basic GROUP BY
- Power BI is only as good as the data it receives — clean first

---

## 📬 Connect

**Harsha Vardhan Chittapragada**
[LinkedIn](https://linkedin.com/in/harshavardhanchittapragada) · [GitHub](https://github.com/harshavardhanchittapragada-max)
