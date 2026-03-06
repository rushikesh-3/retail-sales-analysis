# 🛒 Retail Sales — Exploratory Data Analysis

[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-EDA-150458?logo=pandas)](https://pandas.pydata.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://jupyter.org/)
[![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)](https://powerbi.microsoft.com/)
[![Status](https://img.shields.io/badge/Status-Completed-brightgreen)]()

> **End-to-end exploratory data analysis** on 64,104 retail transactions (Jan 2014 – Feb 2018), covering data wrangling, feature engineering, visual analysis, and business insights — with a Power BI dashboard coming soon.

---

## 📌 Table of Contents
- [Project Overview](#-project-overview)
- [Dataset](#-dataset)
- [Project Workflow](#-project-workflow)
- [Key Findings](#-key-findings)
- [Visualisations](#-visualisations)
- [Tech Stack](#-tech-stack)
- [Repository Structure](#-repository-structure)
- [How to Run](#-how-to-run)
- [Strategic Recommendations](#-strategic-recommendations)
- [Future Work](#-future-work)
- [Connect](#-connect)

---

## 🎯 Project Overview

This project analyses a **multi-table regional sales dataset** to extract business intelligence for a retail company operating across four U.S. regions and three sales channels.

The analysis answers questions such as:
- Which months and seasons drive the most revenue?
- Which products and customers generate the most (and least) value?
- Does a higher unit price lead to higher profit margins?
- Which sales channel and region are most critical — and most at risk?

---

## 🗃️ Dataset

The raw dataset is a **6-table Excel workbook** merged into a single analysis-ready dataframe.

| Table | Description |
|-------|-------------|
| `Sales Orders` | Core transaction records (64,104 rows) |
| `Customers` | 175 unique customer accounts |
| `Products` | 30 SKUs with cost and price info |
| `Regions` | Delivery region mapping |
| `State Regions` | State → Region lookup |
| `Budgets` | 2017 product-level budget targets |

**After merging:** Zero null values confirmed across all joined tables.

> 📁 Raw data: [`data/Regional_Sales_Dataset.xlsx`](data/)

---

## 🔄 Project Workflow

```
Raw Excel (6 tables)
        │
        ▼
  Data Loading & Inspection
  (df.head, df.info, null checks per table)
        │
        ▼
  Data Cleaning
  (drop redundant columns, standardise column names,
   fix dtypes, remove duplicates)
        │
        ▼
  Data Merging
  (6-table left joins into single master dataframe)
        │
        ▼
  Feature Engineering
  ┌─────────────────────────────┐
  │  total_cost = qty × cost    │
  │  profit = revenue − cost    │
  │  profit_margin_pct          │
  │  order_month (period)       │
  └─────────────────────────────┘
        │
        ▼
  Exploratory Data Analysis
  (seasonality, channels, products,
   regions, customers, margins)
        │
        ▼
  Business Insights & Recommendations
        │
        ▼
  Power BI Dashboard (coming soon)
```

---

## 📊 Key Findings

### 1️⃣ Seasonal Patterns
- Revenue **peaks consistently May–August** across all four years
- A **secondary uplift in November–December** aligns with holiday demand
- **January–February** are the weakest months — opportunity for targeted promotions

### 2️⃣ Sales Channel Distribution
| Channel | Revenue Share |
|---------|:---:|
| Wholesale | ~54% |
| Distributor | ~31% |
| Export | ~15% |

> ⚠️ Over-reliance on Wholesale creates strategic concentration risk.

### 3️⃣ Product Performance
- Top 10 products (out of 30) generate the **majority of total revenue**
- **Product 26 and Product 25** are the top two revenue contributors
- ❗ High-revenue products **do not always deliver the highest margins** — cost structure matters more than price

### 4️⃣ Regional Revenue
| Rank | Region | Status |
|------|--------|--------|
| 🥇 1st | West | Top performer |
| 🥈 2nd | South | Strong |
| 📈 3rd | Midwest | Growth opportunity |
| 📈 4th | Northeast | Underserved market |

### 5️⃣ Customer Concentration (Pareto Effect)
- Out of **175 customers**, a small high-frequency cohort drives a disproportionate share of revenue
- Average order value rises sharply with order frequency — classic Pareto 80/20 pattern

### 6️⃣ Pricing ≠ Profitability
- **No strong linear relationship** between unit price and profit margin
- Profitability is driven by **cost management**, not pricing alone

---

## 📸 Visualisations

| Chart | Insight |
|-------|---------|
| 📈 Monthly Revenue Trend | Clear mid-year peak and holiday uplift |
| 🍩 Channel Mix (Pie) | Wholesale dominance visible at a glance |
| 📊 Top 10 Products by Revenue (Bar) | Revenue concentration in top SKUs |
| 📊 Top Products by Margin (Bar) | Margin leaders differ from revenue leaders |
| 🗺️ Revenue by Region (Bar) | West and South outperform |
| 🔵 Order Frequency vs AOV (Scatter) | Pareto cluster of VIP customers |
| 📦 Order Value Distribution (Histogram) | Right-skewed — most orders are small |

> All charts are in the notebook: [`Sales_Analysis.ipynb`](Sales_Analysis.ipynb)

---

## 🧰 Tech Stack

| Tool | Use |
|------|-----|
| Python 3.x | Core analysis |
| Pandas | Data wrangling, merging, groupby |
| NumPy | Numerical operations |
| Matplotlib | Base plotting |
| Seaborn | Statistical visualisations |
| Jupyter Notebook | Interactive development |
| Power BI *(upcoming)* | Business dashboard |

---

## 📁 Repository Structure

```
retail-sales-eda/
│
├── 📓 Sales_Analysis.ipynb              # Full annotated notebook
├── 📝 Sales_EDA_Report.docx             # Detailed written report
├── 📑 Sales_EDA_Presentation.pdf        # Slide deck (PDF)
│
├── 📂 data/
│   └── Regional_Sales_Dataset.xlsx      # Raw multi-sheet dataset
│
├── 📂 visuals/                           # Exported chart images
│   ├── monthly_revenue_trend.png
│   ├── channel_distribution.png
│   ├── top10_products_revenue.png
│   ├── top10_products_margin.png
│   ├── regional_revenue.png
│   └── customer_scatter.png
│
└── README.md
```

> 🔜 `/dashboard/` folder with Power BI `.pbix` file coming soon

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/retail-sales-eda.git
cd retail-sales-eda
```

### 2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```

### 3. Launch the notebook
```bash
jupyter notebook Sales_Analysis.ipynb
```

### 4. Run all cells
Use **Kernel → Restart & Run All** to reproduce the full analysis end-to-end.

---

## 💡 Strategic Recommendations

| # | Recommendation | Rationale |
|---|----------------|-----------|
| 1 | **Seasonal Inventory Planning** | Stock up before May; run promos in Jan–Feb |
| 2 | **Portfolio Rationalisation** | Cut or reposition low-revenue, low-margin SKUs |
| 3 | **Channel Diversification** | Grow Distributor & Export to reduce Wholesale risk |
| 4 | **Regional Expansion** | Target Midwest and Northeast with dedicated campaigns |
| 5 | **VIP Customer Retention** | Protect top-20% accounts with loyalty programmes |
| 6 | **Cost Efficiency Focus** | Margin improvement requires cost audits, not price hikes |

---

## 🔭 Future Work

- [ ] **Time-Series Forecasting** — ARIMA / Facebook Prophet for monthly revenue prediction
- [ ] **Customer Segmentation** — RFM analysis + K-Means clustering
- [ ] **Geospatial Mapping** — Choropleth map of revenue by U.S. state
- [ ] **Budget vs Actual Analysis** — 2017 performance vs targets
- [x] **Power BI Dashboard** — Interactive visuals *(in progress)*

---

## 🧑‍💻 About

Built as part of a **B.Tech Data Science** portfolio to demonstrate end-to-end analytical skills — from raw multi-table data to actionable business insights.

**Skills demonstrated:** `Data Wrangling` · `Feature Engineering` · `EDA` · `Data Visualisation` · `Business Intelligence` · `Python` · `Pandas` · `Seaborn`

---

## 📬 Connect

- 🔗 LinkedIn: [Rushikesh](https://www.linkedin.com/in/nangaaji-rushikesh/)
- 📧 Email: rushikeshnangaaji@gmail.com

---

*⭐ If you found this useful, consider giving it a star!*
