# 🦠 COVID-19 Global Pandemic Analysis & Time-Series EDA

## 📌 Project Overview
This project is an end-to-end Exploratory Data Analysis (EDA) of the COVID-19 pandemic. The objective was to extract three separate, messy datasets (Confirmed Cases, Deaths, and Recoveries), engineer them into a unified chronological format, and generate business-ready insights regarding transmission velocity, regional disparities, and healthcare operational efficiency.

## 🛠️ Data Engineering & Preprocessing (The Heavy Lifting)
Raw epidemiological data is notoriously difficult to work with. A significant portion of this project was dedicated to complex data wrangling using **Pandas**. 

Here are the specific data cleaning protocols applied:
* **Header Standardization & Indexing:** The raw `deaths` and `recovered` datasets contained blank/messy formatting in the first row. I bypassed this using `header=1` during ingestion, and utilized `.iloc[0]` combined with `.drop(0).reset_index()` to dynamically reassign correct column names and reset the dataframe index.
* **Dimensionality Transformation (`pd.melt`):** The original data was provided in a "wide" format (where every single date from Jan 2020 to May 2021 was its own column—nearly 500 columns). To perform time-series analysis, I used `pd.melt()` to unpivot the data into a "long" format. I locked the geographical keys (`['Province/State', 'Country/Region', 'Lat', 'Long']`) while collapsing the dates into a single, analyzable `Date` feature.
* **Intelligent Missing Value Imputation (`.fillna`):** * Many nations report data at the federal level, leaving the `Province/State` column blank. Instead of dropping `NaN` values and losing critical data, I imputed them with the string `"All Province"` to preserve data integrity.
  * Missing geographical coordinates (`Lat`, `Long`) were isolated and filled with `0` to prevent computation errors during plotting.
* **Data Type Casting:** Casted the unpivoted date strings into robust Datetime objects using `pd.to_datetime(format='%m/%d/%y', errors='coerce')`, and forced case counts into standard `int64` formats.
* **Granular Aggregation (`.groupby`):** Because large nations reported data split by province, I utilized `.groupby(['Country/Region', 'Date']).sum()` to aggregate state-level data into accurate, unified national daily totals.

## 📊 Key Visualizations & Analytical Insights
Once the data pipeline was clean, I utilized **Matplotlib and Seaborn** to build professional, corporate-styled visualizations to answer core epidemiological questions:
* **The Inflection Point (China Trajectory):** Visualized the early-stage cumulative curve to identify the exact timeframe where exponential growth transitioned into a plateau, quantifying the success of early containment protocols.
* **Transmission Volatility (European Markets):** Plotted daily new cases for Germany, France, and Italy. This time-series analysis highlighted high-frequency volatility, mapping the direct impact of variant waves and policy changes over time.
* **Regional Disparities (Canadian Drill-Down):** Executed a granular geographic drill-down, comparing the Death Rates across Canadian provinces. This proved that national aggregates often hide localized healthcare crises.
* **Healthcare Efficiency (US Recovery Ratio):** Engineered a new KPI—the month-over-month "Recovery Ratio." By plotting this as a trend line, the analysis moved beyond raw case counts to actually measure how the operational efficiency of the US healthcare system fluctuated throughout the pandemic.

## 💻 Tech Stack
* **Language:** Python
* **Data Wrangling:** Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn
