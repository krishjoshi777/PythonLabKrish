# 🦠 COVID-19 Data Analysis — Experiment 19-20
---

## 👤 Student Details

| Field | Details |
|---|---|
| **Name** | Krish Joshi |
| **PRN** | 25070123064 |
| **Class** | EnTC A3 |
| **Batch** | 2025–2029 |
| **Experiment** | 19–20 (Project Analysis) |

---

## 📌 Overview

This project performs an **end-to-end exploratory data analysis (EDA)** of the COVID-19 pandemic dataset. It covers global and India-specific trends, interactive world map visualizations, and country/state-level case breakdowns using real-world data.

The analysis uncovers patterns in **Confirmed**, **Recovered**, **Deaths**, and **Active** cases across countries and Indian states — helping build an intuition for large-scale public health data.

---

## 🎯 Objectives

- Load, clean, and preprocess COVID-19 time-series data
- Engineer new features such as **Active Cases**
- Analyze global trends and identify the most impacted countries
- Drill down into **India-specific** data at the state level
- Visualize findings using **interactive choropleth maps** with Plotly

---

## 🗂️ Dataset

- **File:** `covid_19_data.csv`
- **Key Columns:**
  - `ObservationDate` — Date of recorded data
  - `Country/Region` — Country name
  - `Province/State` — State/Province (where available)
  - `Confirmed` — Total confirmed cases
  - `Deaths` — Total deaths
  - `Recovered` — Total recovered cases

> 📎 Dataset Source: [Kaggle — COVID-19 Dataset](https://www.kaggle.com/datasets/sudalairajkumar/novel-corona-virus-2019-dataset)

---

## 🛠️ Tech Stack

| Library | Purpose |
|---|---|
| `pandas` | Data loading, cleaning, and manipulation |
| `numpy` | Numerical operations |
| `matplotlib` | Static plotting |
| `seaborn` | Statistical visualizations |
| `plotly.express` | Interactive choropleth world maps |
| `sklearn` | Train-test split (imported for future ML extension) |

---

## 📂 Project Structure

The repository contains the main Jupyter Notebook (`Covid_data_analysis.ipynb`), the dataset file (`covid_19_data.csv`), and this `README.md` documentation file.

---

## 🔬 Methodology

### 1️⃣ Import Libraries
All necessary libraries — `pandas`, `numpy`, `matplotlib`, `seaborn`, `plotly`, and `sklearn` — are imported to support data manipulation, visualization, and future ML extensions.

### 2️⃣ Load & Preview Data
The dataset is loaded from a CSV file and previewed to understand its structure and contents.

### 3️⃣ Data Cleaning
Irrelevant columns (`SNo`, `Last Update`) are dropped. The `ObservationDate` column is converted to `datetime64`, and `Confirmed`, `Deaths`, and `Recovered` columns are filled with zeros for any missing values and cast to `int64`.

### 4️⃣ Feature Engineering — Active Cases
A new **Active Cases** column is derived as:
> **Active Cases** = Confirmed − Recovered − Deaths

### 5️⃣ Latest Date Snapshot
The dataset is filtered to retain only records from the most recent observation date, ensuring all analysis reflects the latest available state.

### 6️⃣ Country-Level Aggregation
Records are grouped by `Country/Region` and summed to get total Confirmed, Deaths, Recovered, and Active cases per country.

### 7️⃣ India-Specific Analysis
India's data is isolated and missing `Province/State` values are filled using the mode. A state-wise ranking is generated based on confirmed cases to identify the most affected states.

### 8️⃣ Interactive World Maps
Choropleth maps are generated using `plotly.express` — one for **Confirmed** cases (red scale) and one for **Recovered** cases (green scale) — providing a global visual overview.

### 9️⃣ India Choropleth Map
A zoomed Asia-scoped choropleth map is plotted specifically for India to highlight its position in the regional context.

---

## 📊 Key Insights

- ✅ Successfully identified the **top 20 countries** with highest confirmed and recovered cases
- 🇮🇳 Performed a **state-level breakdown** of India's COVID-19 data
- 🗺️ Generated **interactive choropleth maps** for global confirmed and recovered cases
- 🔢 Engineered the **Active Cases** metric from raw data
- 📅 All analysis is anchored to the **latest available date** in the dataset for accuracy

---

## ▶️ How to Run

1. **Clone the repository** — Download or clone this repo to your local machine.
2. **Install dependencies** — Install the required libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `plotly`, and `scikit-learn` using pip.
3. **Add the dataset** — Place `covid_19_data.csv` in the same directory as the notebook, or update the file path inside the notebook accordingly.
4. **Launch the notebook** — Open `Covid_data_analysis.ipynb` in Jupyter Notebook, JupyterLab, or directly in **Google Colab** for a zero-setup experience.

---

## 🚀 Possible Extensions

- 📈 Time-series forecasting using ARIMA or Prophet
- 🤖 Machine learning models to predict case spikes
- 📊 Dashboard using Streamlit or Dash
- 🌐 API integration for live data fetching

---

## 🧾 Conclusion

This experiment successfully demonstrates the power of **Python-based data analysis** applied to a real-world public health crisis. By working with the COVID-19 dataset, the following was achieved:

- **Data preprocessing** techniques were applied to handle missing values, fix data types, and drop redundant columns, resulting in a clean, analysis-ready dataset.
- A new **Active Cases** feature was engineered from existing columns, adding meaningful insight beyond the raw data.
- **Country-level and state-level aggregations** revealed which regions were most severely impacted during the peak of the pandemic.
- **Interactive choropleth maps** built with Plotly provided an intuitive, visual understanding of the global and India-specific spread of the virus.

Overall, this project highlights how data science tools can transform raw epidemiological data into actionable insights — a skill that is directly applicable to fields like healthcare analytics, public policy, and crisis management. It also reinforces core data science competencies including EDA, feature engineering, groupby aggregations, and geospatial visualization.

---

<div align="center">
   <strong>Krish Joshi</strong> | EnTC A3 | PRN: 25070123064 | Batch 2025–2029
</div>
