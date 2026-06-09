# 🦠 COVID-19 Global Pandemic Analytics: Python EDA

**TL;DR:** An end-to-end Exploratory Data Analysis (EDA) of global COVID-19 data. I built a Python data pipeline to ingest, clean, and transform messy, multi-dimensional epidemiological datasets into business-ready insights. **Key achievement:** Engineered a custom "Month-over-Month Recovery Ratio" metric to track true healthcare operational efficiency, moving beyond standard cumulative case counting.

### 📊 Project Highlights
[*(Replace this text with a screenshot of your US Recovery Ratio line chart)*](https://github.com/iaarifpathan/Python-Project/blob/main/Covid-19%20Global%20Analytics/canada_provinces.png)
*(Replace this text with a screenshot of your Canadian Provinces bar chart)*

---

## 🛠️ Data Engineering & Wrangling (The Heavy Lifting)
The raw datasets provided by global health organizations were highly unstructured and stored in a "wide" format. I utilized **Python (Pandas)** to execute complex data cleaning pipelines before any analysis could begin:

* **Header Repair & Indexing:** Bypassed corrupted initial rows in the `deaths` and `recovered` files by utilizing `header=1`, combined with `.iloc[0]` and `.reset_index(drop=True)` to dynamically rebuild the dataframes.
* **Dimensionality Transformation (`pd.melt`):** The raw data contained over 400 individual date columns. I utilized `pd.melt()` to unpivot this massive dataset into a highly structured "long" chronological format, locking geographic keys to enable accurate time-series analysis.
* **Intelligent Imputation (`.fillna`):** Handled severe data inconsistencies where federal-level reporting left provincial columns blank. Imputed missing values with `"All Province"` to preserve data integrity for national aggregations.
* **Granular Aggregation (`.groupby`):** Casted string dates to Pandas `Datetime` objects and used `.groupby()` to aggregate state-level data into accurate national daily totals.

## 📈 Key Analytical Insights
Using **Matplotlib** and **Seaborn**, I built corporate-grade visualizations to answer core epidemiological questions:

1. **Global Infection Trajectories:** Mapped the initial exponential growth of the **Top 5 most affected nations**, identifying the exact inflection points where containment protocols took effect.
2. **European Transmission Volatility:** Plotted daily new cases across Germany, France, and Italy, mapping the high-frequency volatility of variant waves over time.
3. **Engineered KPI - US Recovery Ratio:** Instead of plotting simple cumulative cases, I calculated and plotted a **Month-over-Month Recovery Ratio**, revealing the true operational efficiency of the US healthcare system over the course of the pandemic.
4. **Geographic Drill-Down (Canada):** Benchmarked fatality rates across Canadian provinces, proving that national averages often hide massive localized healthcare crises.
5. **Healthcare Efficacy (Australia vs. Canada):** Created a standardized, side-by-side comparison of recovery rates between the two nations, bypassing raw population differences.
6. **Mortality Extremes:** Isolated the **Top 3 absolute highest fatality rates** (Yemen, Mexico, and MS Zaandam) to highlight the most extreme public health failures.

## 💡 Business Value
This project demonstrates how raw, disconnected data can be transformed into actionable strategy. By tracking metrics like the "Recovery Ratio" and identifying regional fatality outliers, stakeholders can pinpoint exactly where a healthcare system is losing efficiency, allowing for targeted deployment of emergency funding, ventilators, and medical personnel.

**Tech Stack:** Python | Pandas | Matplotlib | Seaborn | Jupyter Notebook
