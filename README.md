\# Retail Sales Performance Analysis \\\& Interactive Dashboard



\## Project Overview



This repository contains an end-to-end data cleaning, analytical pipeline, and interactive business intelligence web application for fulfilled retail transactions. Built using Python, Pandas, Plotly Express, and Streamlit, the application cleans raw transactional records across multiple master files and provides real-time key performance metrics.



\### Project Deliverables



\* \*\*`Executive Summary.txt`\*\*: High-level bulleted summary detailing primary business performance findings and metric breakdowns.

\* \*\*`YourNotebook.ipynb`\*\*: Complete Jupyter Notebook covering exploratory data analysis (EDA), data cleaning procedures, and chart prototyping.

\* \*\*`Cleaned\\\_customers.csv`\*\*: Standardized customer master file containing deduplicated records, regional groupings, and loyalty tier information.

\* \*\*`Cleaned\\\_products.csv`\*\*: Normalized product catalog featuring cleaned category mappings and brand details.

\* \*\*`5+ exported charts (PNG)`\*\*: High-resolution chart exports covering monthly trends, product category sales, regional breakdowns, order value distributions, sales channels, and top 10 products.



\\---



\## Data Analysis \\\& Methodology



The data pipeline processes raw CSV files (`customers.csv`, `products.csv`, `orders.csv`, and `order\\\_items.csv`) through the following steps:



1\. \*\*Deduplication \\\& Category Normalization\*\*:



&#x20;  \* Removed exact duplicate records across all source datasets.

&#x20;  \* Standardized messy and abbreviated category entries (e.g., mapping `"elec"`, `"electronics"` to `"Electronics"`, and `"fashon"` to `"Fashion"`).

2\. \*\*Data Cleaning \\\& Type Conversion\*\*:



&#x20;  \* Cleaned currency strings (removing `₱`, commas, and whitespace) via custom helper function `clean\\\_money()` to convert monetary strings into numeric floats.

&#x20;  \* Parsed mixed datetime formats in order timestamps (`order\\\_datetime` $\\\\rightarrow$ `order\\\_date`).

&#x20;  \* Filtered out non-positive quantities ($\\\\text{quantity} \\\\le 0$) and unparseable prices/dates.

&#x20;  \* Handled missing discount values by filling missing instances with `0` and enforcing valid ranges ($0 \\\\le \\\\text{discount\\\_pct} \\\\le 1$).

3\. \*\*Referential Integrity \\\& Scope Filtering\*\*:



&#x20;  \* Validated foreign keys across tables, dropping unlinked order items or orders missing corresponding customer or product records.

&#x20;  \* Filtered analysis strictly to fulfilled transactions where `order\\\_status` is either `"Completed"` or `"Shipped"`.

4\. \*\*Analytical Calculations\*\*:



&#x20;  \* \*\*Gross Sales\*\*: Computed as $\\\\text{Quantity} \\\\times \\\\text{Unit Price}$.

&#x20;  \* \*\*Net Sales\*\*: Computed as $\\\\text{Gross Sales} \\\\times (1 - \\\\text{Discount Percentage})$.

&#x20;  \* \*\*Average Order Value (AOV)\*\*: Computed strictly at the \*\*Order level\*\* by aggregating Net Sales per `order\\\_id` before taking the mean (preventing line-item level skewness).



\\---



\## Key Takeaways



\* \*\*Fulfillment Accuracy\*\*: Isolating fulfilled orders ("Completed" and "Shipped") provides an un-skewed representation of realized revenue versus total attempted cart checkouts.

\* \*\*Order-Level Aggregation\*\*: Evaluating Average Order Value (AOV) at the order level accurately reflects customer basket sizes rather than individual item prices.

\* \*\*Data Standardization Impact\*\*: Resolving string formatting issues (such as currency symbols and mixed date formats) restored valid records that would otherwise be lost to parsing errors.



\\---



\## Insights



\* \*\*Category Revenue Drivers\*\*: Product category standardization reveals which core categories generate the majority of overall gross sales.

\* \*\*Regional Distribution\*\*: Regional grouping shows distinct concentration patterns of sales across geographical zones.

\* \*\*Channel Performance\*\*: Comparing sales channels identifies primary revenue acquisition sources across direct and third-party routes.

\* \*\*Order Value Spread\*\*: Histogram distribution of net order values shows customer purchase volume patterns across pricing tiers.



\\---



\## Summary



The Streamlit dashboard (`app.py`) provides an interactive interface to explore retail performance metrics. Users can dynamically filter datasets by \*\*Month\*\*, \*\*Region\*\*, \*\*Sales Channel\*\*, and \*\*Product Category\*\*. The system auto-recalculates four key KPIs (Gross Sales, Fulfilled Orders, Average Order Value, and Top Category) alongside five analytical Plotly charts and an expandable filtered transaction table.



\\---



\## Conclusions



\* Rigorous data wrangling and referential integrity checks ensure financial KPIs are derived exclusively from verified, fulfilled transactions.

\* Normalizing raw inputs (categories, currency formats, discounts) is critical for reliable multi-dimensional filtering.

\* Clear distinctions between Gross and Net Sales highlight the overall financial impact of promotional order discounts.



\\---



\## Recommendations



1\. \*\*Inventory Alignment\*\*: Focus stock replenishment on top-performing products and categories identified in the top 10 breakdown.

2\. \*\*Channel Optimization\*\*: Focus marketing allocation on high-performing sales channels while reviewing lower-volume channels for operational adjustments.

3\. \*\*Targeted Regional Strategy\*\*: Tailor regional promotions and logistics based on regional gross sales distributions.

4\. \*\*Discount Guardrails\*\*: Monitor net sales margins across high-discount orders to preserve profitability while maintaining order volume.





"# pythonprogramming_data_analysis" 
