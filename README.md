# CodeAlpha Data Analytics Internship — Task 3: Data Visualization

## Executive Business Analytics & Visual Storytelling Report

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Plots-4c72b0)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 📌 1. Official Task 3 Objective

According to the official **CodeAlpha Data Analytics Internship** guidelines:
* **Task Title:** Task 3 — Data Visualization
* **Core Directives:**
  * Transform raw transactional data into meaningful visual formats like charts, graphs, and multi-metric dashboards.
  * Use industry-standard Python visualization libraries such as **Matplotlib** and **Seaborn**.
  * Design visuals that enhance understanding, highlight anomalies, and reveal hidden trends.
  * Craft compelling data stories that directly support strategic business decision-making.
  * Build an impactful, publication-ready portfolio project with clean code and robust interpretations.

---

## 📂 2. Repository Structure

```text
CodeAlpha_Task3/
├── .gitignore                               # Standard Git ignore file for Python/Jupyter
├── CodeAlpha_Task3_Data_Visualization.ipynb # Complete, executed Jupyter Notebook with all outputs
├── README.md                                # Comprehensive project documentation & business report
├── requirements.txt                         # Python package dependencies
└── superstore_sales.csv                     # Official US Superstore dataset (9,994 records)
```

---

## 📊 3. Dataset Information & Acquisition

### Overview
This project utilizes the **US Superstore Retail Dataset**, an industry-standard commercial dataset containing 4 years of retail transaction history across North America.

* **Total Records:** 9,994 transactions
* **Total Attributes:** 21 variables
* **Temporal Coverage:** January 3, 2015 – December 30, 2018
* **Integrity:** Zero missing values across all core numerical, categorical, and date fields.

### Key Attributes
| Field Name | Type | Description |
|:---|:---|:---|
| `Order ID`, `Order Date`, `Ship Date` | String / DateTime | Transaction identification and timeline metrics |
| `Ship Mode` | Categorical | Delivery method (Standard, Second Class, First Class, Same Day) |
| `Customer ID`, `Customer Name`, `Segment`| Categorical | Customer identifiers and classification (Consumer, Corporate, Home Office) |
| `Country`, `City`, `State`, `Region` | Categorical | Geographic location across 4 sales territories (West, East, Central, South) |
| `Category`, `Sub-Category`, `Product ID`| Categorical | Product taxonomy (Furniture, Office Supplies, Technology; 17 sub-categories) |
| `Sales`, `Quantity`, `Discount`, `Profit` | Numerical | Transaction revenue, units sold, discount applied (0–80%), and net profit |
| `Profit Margin (%)` *(Engineered)* | Numerical | Derived financial ratio: `(Profit / Sales) * 100` |
| `Shipping Days` *(Engineered)* | Numerical | Lead time between order creation and carrier dispatch |

### Dataset Acquisition
The dataset is bundled directly inside this repository as `superstore_sales.csv`. If needed externally, it is publicly accessible from:
* [GitHub Gist / Raw Superstore CSV](https://gist.githubusercontent.com/nnbphuong/38db511db14542f3ba9ef16e69d3814c/raw/3a77ff9d97c504d3ec3210b12fde7242b8c6ab63/Superstore.csv)
* [Tableau Community Sample Superstore Dataset](https://community.tableau.com/s/sample-data)

---

## 📈 4. Baseline Executive Metrics (Actual Calculated Results)

All statistics are strictly calculated from the verified dataset without fabrication:

* **Total Gross Revenue:** `$2,297,200.86`
* **Total Net Profit:** `$286,397.02`
* **Overall Net Profit Margin:** `12.47%`
* **Total Units Sold:** `37,873 units`
* **Total Unique Orders Fulfilled:** `5,009 orders`
* **Total Unique Active Customers:** `793 customers`

---

## 🎨 5. Visualizations Implemented & Data Stories

The project develops 7 distinct visual modules, progressing from macro-temporal trends to micro-level pricing elasticity and an executive scorecard:

### 1. Time-Series Trend Analysis (Dual-Axis Line Chart)
* **Design:** Monthly gross sales plotted against net profit across 48 months with distinct color-coding, markers, and secondary Y-axis.
* **Finding:** Strong recurring fourth-quarter seasonality (annual revenue surges in November and December). Baseline sales expanded steadily year-over-year from 2015 to 2018. However, peak revenue months experienced slight margin dilution due to high holiday discounting.

### 2. Product Portfolio Profitability (Comparative Horizontal Bar Charts)
* **Design:** Side-by-side horizontal bar charts comparing gross sales vs. net profit across all 17 sub-categories with value annotations and conditional green/red formatting.
* **Finding:** 
  * **Profit Engines:** Copiers (`+$55,618`), Phones (`+$44,516`), and Accessories (`+$41,937`) deliver high margins.
  * **Severe Loss Bleeds:** Tables generated `$206,966` in sales but incurred a **net loss of -$17,725**; Bookcases generated `$114,880` with a **net loss of -$3,473**. High volume does not guarantee profitability.

### 3. Market Demographics & Territorial Distribution (Donut & Grouped Bar Chart)
* **Design:** Donut chart illustrating customer segment sales distribution alongside a dual-bar chart assessing territorial sales vs. net profits.
* **Finding:** 
  * The Consumer segment represents **50.6%** (`$1.16M`) of sales, with all segments generating healthy 12–14% margins.
  * The West region is the top performer (`$725K` sales, `$108K` profit, ~`14.9%` margin). In contrast, the Central region generated `$501K` in sales but only `$39.7K` in profit (~`7.9%` margin)—less than half the profit efficiency of the West.

### 4. Pricing Dynamics & Discount Elasticity (Scatter Plot & Tiered Bar Chart)
* **Design:** Transaction scatter plot with category hues and a 20% threshold marker, paired with an average profit bar chart across discount tiers.
* **Finding:** 
  * **The 20% Discount Cliff:** Discounts at or below 20% generate positive returns (`+$24` to `+$67` average profit per order).
  * **Margin Destruction:** Discounts above 20% cause severe, escalating losses (`-$46.6` at 30%, `-$176.4` at 50%, and `-$330.2` at 70% discount). Furniture items are especially vulnerable to steep losses under discount pressure.

### 5. Profit Dispersion & Outlier Analysis (Box Plots with Mean Markers)
* **Design:** Box-and-whisker plot displaying median, interquartile ranges (IQR), and positive/negative outlier points across categories, enhanced with custom mean markers.
* **Finding:** Furniture exhibits high margin volatility with its lower quartile extending into negative territory. Office Supplies represents a dependable, low-variance baseline. Technology demonstrates the greatest upside potential driven by high-value enterprise orders.

### 6. Correlation Matrix & Regional Cross-Tabulation (Heatmap Suite)
* **Design:** Annotated Pearson correlation matrix paired with a Category × Territory pivot table heatmap.
* **Finding:** 
  * Statistically confirms a strong negative correlation of **-0.86** between `Discount` and `Profit Margin (%)`.
  * Pinpoints a critical regional deficit: **Central Region Furniture incurred a net cumulative loss of -$2,871**, while all other region-category combinations generated net profits.

### 7. Executive Business Performance Dashboard (4-Panel Grid Layout)
* **Design:** Unified multi-panel layout constructed using Matplotlib's `GridSpec`:
  * *Panel A:* KPI Scorecard (Revenue, Profit, Margin %, Orders).
  * *Panel B:* Category Gross Sales vs. Net Profit.
  * *Panel C:* 4-Year Annual Revenue and Profit Growth Trajectory.
  * *Panel D:* Territorial Share of Total Net Profit.
* **Finding:** Provides C-suite stakeholders with an immediate, holistic assessment of commercial health, margin risks, and geographic strengths.

---

## 💡 6. Strategic Recommendations for Decision-Makers

1. **Enforce an Automated 20% Discount Ceiling:** Restrict sales representatives from exceeding 20% discounts without senior managerial override, directly eliminating the primary driver of negative-profit transactions.
2. **Restructure Loss-Leading Furniture Lines:** Address the `-$17,725` deficit in Tables by renegotiating manufacturer supply costs, passing oversized freight charges to buyers, or bundling tables with high-margin technology accessories.
3. **Replicate the West Territory's Operational Blueprint:** Align the Central region's pricing, discount governance, and fulfillment models with the high-performing West territory to lift regional profit margins from 7.9% toward the 14%+ benchmark.
4. **Advance Inventory Ahead of Q4 Peaks:** Pre-position stock for high-margin sub-categories (Copiers, Phones, Storage) prior to November to satisfy peak demand at full retail margin without relying on clearance promotions.

---

## 🚀 7. Installation & Reproducibility Guide

Follow these steps to run the project locally:

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/CodeAlpha_Data_Visualization.git
cd CodeAlpha_Data_Visualization
```

### 2. Set Up a Virtual Environment (Recommended)
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Launch the Jupyter Notebook
```bash
jupyter notebook CodeAlpha_Task3_Data_Visualization.ipynb
```
*Run all cells sequentially (`Cell -> Run All`) to reproduce all data tables, KPI calculations, and interactive visualizations.*

---

## 📋 8. Submission Compliance Checklist

- [x] Official CodeAlpha Task 3 verified from internship instruction document.
- [x] Dedicated, clean repository containing only necessary project files.
- [x] Completely isolated from previous tasks (Task 2 untouched).
- [x] Real-world public dataset verified, loaded, and documented.
- [x] All 7 visualization modules built using Matplotlib and Seaborn.
- [x] Notebook executed end-to-end with zero errors and all visual outputs preserved.
- [x] Clear data stories, actionable business recommendations, and beginner-friendly comments included.
- [x] Ready for GitHub submission under repository naming convention `CodeAlpha_Data_Visualization`.
