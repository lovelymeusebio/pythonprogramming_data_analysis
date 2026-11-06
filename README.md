# 🛒 Retail Sales Performance Analysis & Interactive Dashboard

![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)

An end-to-end data cleaning, analytical pipeline, and interactive business intelligence web application for fulfilled retail transactions. Built using Python, Pandas, Plotly Express, and Streamlit, the application cleans raw transactional records across multiple master files and provides real-time key performance metrics.

---

## 📌 Table of Contents
- [Project Overview](#-project-overview)
- [Project Deliverables](#-project-deliverables)
- [Tech Stack](#-tech-stack)
- [Repository Structure](#-repository-structure)
- [Data Analysis & Methodology](#-data-analysis--methodology)
- [Key Takeaways & Insights](#-key-takeaways--insights)
- [Interactive Dashboard Features](#-interactive-dashboard-features)
- [Conclusions & Strategic Recommendations](#-conclusions--strategic-recommendations)
- [Getting Started](#-getting-started)

---

## 📖 Project Overview

This project cleans messy transactional retail data, enforces strict business logic (such as filtering strictly to completed/shipped transactions), normalizes raw category and financial metadata, and exposes the processed data through an interactive dashboard. 

The analytical pipeline transforms unstructured or error-prone transactional raw files into actionable financial and operational business intelligence.

---

## 📦 Project Deliverables

* **`Executive Summary.txt`**: High-level summary detailing primary business performance findings and metric breakdowns.
* **`YourNotebook.ipynb`**: Complete Jupyter Notebook covering exploratory data analysis (EDA), data cleaning procedures, and chart prototyping.
* **`Cleaned_customers.csv`**: Standardized customer master file containing deduplicated records, regional groupings, and loyalty tier information.
* **`Cleaned_products.csv`**: Normalized product catalog featuring cleaned category mappings and brand details.
* **`5+ Exported Charts (PNG)`**: High-resolution chart exports covering monthly trends, product category sales, regional breakdowns, order value distributions, sales channels, and top 10 products.

---

## 🛠️ Tech Stack

* **Language:** Python 3.9+
* **Data Processing & Analytics:** Pandas, NumPy
* **Data Visualization:** Plotly Express, Matplotlib / Seaborn
* **Web Dashboard:** Streamlit
* **Environment:** Jupyter Notebook / VS Code

---

## 📁 Repository Structure

```text
.
├── Executive Summary.txt
├── YourNotebook.ipynb
├── Cleaned_customers.csv
├── Cleaned_products.csv
├── app.py
├── data/
│   ├── raw/
│   │   ├── customers.csv
│   │   ├── products.csv
│   │   ├── orders.csv
│   │   └── order_items.csv
├── charts/
│   ├── monthly_trends.png
│   ├── category_sales.png
│   ├── regional_breakdown.png
│   ├── order_value_distribution.png
│   └── top_10_products.png
├── README.md
└── requirements.txt
```

---

## ⚙️ Data Analysis & Methodology

The data pipeline processes raw CSV datasets (`customers.csv`, `products.csv`, `orders.csv`, and `order_items.csv`) through four key ETL stages:

### 1. Deduplication & Category Normalization
* Removed exact duplicate records across all source datasets.
* Standardized messy and abbreviated category entries (e.g., mapping `"elec"` and `"electronics"` to `"Electronics"`, and `"fashon"` to `"Fashion"`).

### 2. Data Cleaning & Type Conversion
* Cleaned currency strings (removing `₱`, commas, and whitespace) via custom helper function `clean_money()` to convert monetary values into numeric floats.
* Parsed mixed datetime formats in order timestamps (`order_datetime` $\rightarrow$ `order_date`).
* Filtered out non-positive quantities ($\text{Quantity} \le 0$) and unparseable prices/dates.
* Handled missing discount values by filling missing instances with `0` and enforcing valid ranges ($0 \le \text{discount\_pct} \le 1$).

### 3. Referential Integrity & Scope Filtering
* Validated foreign keys across tables, dropping unlinked order items or orders missing corresponding customer or product records.
* Filtered analysis strictly to fulfilled transactions where `order_status` is either `"Completed"` or `"Shipped"`.

### 4. Analytical Calculations
* **Gross Sales:** $\text{Gross Sales} = \text{Quantity} \times \text{Unit Price}$
* **Net Sales:** $\text{Net Sales} = \text{Gross Sales} \times (1 - \text{Discount Percentage})$
* **Average Order Value (AOV):** Computed strictly at the **Order level** by aggregating Net Sales per `order_id` before calculating the mean, preventing line-item level skewness.

---

## 💡 Key Takeaways & Insights

* **Fulfillment Accuracy:** Isolating fulfilled orders ("Completed" and "Shipped") provides an un-skewed representation of realized revenue versus total attempted cart checkouts.
* **Order-Level Aggregation:** Evaluating Average Order Value (AOV) at the order level accurately reflects customer basket sizes rather than individual item prices.
* **Data Standardization Impact:** Resolving string formatting issues (such as currency symbols and mixed date formats) restored valid records that would otherwise be lost to parsing errors.
* **Category Revenue Drivers:** Product category standardization reveals which core categories generate the majority of overall gross sales.
* **Regional & Channel Distribution:** Regional grouping and channel performance analyses highlight geographical concentration patterns and primary customer acquisition routes.

---

## 📊 Interactive Dashboard Features

The Streamlit application (`app.py`) provides an intuitive dashboard for interactive data exploration:

- **Dynamic Filters:** Filter by **Month**, **Region**, **Sales Channel**, and **Product Category**.
- **Real-Time Key Metrics (KPIs):** Auto-recalculates **Gross Sales**, **Fulfilled Orders**, **Average Order Value**, and **Top Category**.
- **Interactive Visualizations:** Includes 5 dynamic Plotly charts detailing trends, category performance, regional revenue splits, order distribution histograms, and top products.
- **Data Inspection:** An expandable preview table for inspecting filtered transaction records in real time.

---

## 🎯 Conclusions & Strategic Recommendations

### Conclusions
1. Rigorous data wrangling and referential integrity checks ensure financial KPIs are derived exclusively from verified, fulfilled transactions.
2. Normalizing raw inputs (categories, currency formats, discounts) is critical for reliable multi-dimensional filtering.
3. Clear distinctions between Gross and Net Sales highlight the overall financial impact of promotional order discounts.

### Recommendations
1. **Inventory Alignment:** Focus stock replenishment on top-performing products and categories identified in the top 10 breakdown.
2. **Channel Optimization:** Focus marketing allocation on high-performing sales channels while reviewing lower-volume channels for operational adjustments.
3. **Targeted Regional Strategy:** Tailor regional promotions and logistics based on regional gross sales distributions.
4. **Discount Guardrails:** Monitor net sales margins across high-discount orders to preserve profitability while maintaining order volume.

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Streamlit Dashboard
```bash
streamlit run app.py
```"# pythonprogramming_data_analysis" 
