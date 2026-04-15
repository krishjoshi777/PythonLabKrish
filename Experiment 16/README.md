# Lab Experiment Journal: Basic Charts and Visual Encoding using Matplotlib & Seaborn

---

## Experiment Details

| Field | Value |
|---|---|
| **Experiment Title** | Basic Charts and Visual Encoding using Matplotlib & Seaborn |
| **Date** | 2026-04-08 |
| **Student Name** | Krish Joshi |
| **PRN** | 25070123064 |
| **Batch** | EnTC A3 |
| **Experiment No.** | 16 |
| **Programming Language** | Python 3.x |
| **Libraries Used** | matplotlib, seaborn, pandas, numpy |

---

## 1. Objective

To understand and implement data visualisation techniques in Python using Matplotlib and Seaborn, including:

- Creating line charts to visualise trends over time
- Building bar charts for categorical comparisons
- Plotting histograms to understand value distributions
- Using scatter plots to explore relationships between numeric variables
- Applying colour encoding and conditional formatting to communicate additional data dimensions
- Using advanced Seaborn charts (pairplot, heatmap, violin, KDE, etc.) to gain deeper analytical insight
- Composing multi-panel dashboards using `plt.subplots()`

---

## 2. Prerequisites

- Python 3.x installed
- Required libraries:

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
import numpy as np
```

| Library | Install Command |
|---|---|
| matplotlib | `pip install matplotlib` |
| seaborn | `pip install seaborn` |
| pandas | `pip install pandas` |
| numpy | `pip install numpy` |

---

## 3. Datasets Used

| Dataset | Columns | Key Features |
|---|---|---|
| **Dataset 1** | Days, Study_Hours, Marks, Attendance, Sleep_Hours, Assignment_Completed | 5 rows of student daily performance; used for basic line, bar, histogram, scatter charts |
| **Dataset 2** | Day, Region, Sales, Profit, Customers, Category | 10 rows of sales data across 4 regions and 3 categories; intermediate multi-chart practice |
| **Dataset 3** | Day, Region, Category, Sales, Profit, Customers, Rating | 42 rows randomly generated; used for advanced Seaborn charts (pairplot, heatmap, violin, boxen, etc.) |

---

## 4. Experiment Sections

| No. | Section | Dataset | Charts Produced |
|---|---|---|---|
| 4.1 | Matplotlib — Dataset 1 | Student Performance (5 rows) | Line, advanced line, bar, bar with labels, grouped bar, histogram, scatter, conditional scatter |
| 4.2 | Seaborn — Dataset 1 | Student Performance (5 rows) | Lineplot, histplot |
| 4.3 | Matplotlib — Dataset 2 | Sales Performance (10 rows) | Line, advanced line, bar, bar with labels, grouped bar, histogram, scatter, conditional scatter (category-wise) |
| 4.4 | Seaborn — Dataset 2 | Sales Performance (10 rows) | Lineplot, histplot, scatterplot with hue |
| 4.5 | Advanced Seaborn — Dataset 3 | Extended Sales Data (42 rows) | Pairplot, heatmap, violin, boxen, strip, swarm, FacetGrid, KDE, countplot, barplot, lineplot with markers, 2×3 dashboard subplots |

---

## 5. Experiment Sections (Detailed)

### 5.1 Matplotlib Visualisations — Dataset 1 (Student Performance)

**Purpose:** Explore the fundamental Matplotlib chart types on a small, familiar dataset.

**Data Structure:**

```python
data = {
    'Days': ['Mon', 'Tue', 'Wed', 'Thru', 'Fri'],
    'Study_Hours': [2, 3, 2.5, 4, 3.5],
    'Marks': [50, 60, 55, 70, 65],
    'Attendance': [60, 70, 65, 80, 75],
    'Sleep_Hours': [6, 7, 6, 8, 7],
    'Assignment_Completed': [1, 2, 1, 3, 2]
}
```

#### Line Chart — Study Hours Over Days

```python
plt.plot(df['Days'], df['Study_Hours'], marker='o', color='green', linestyle='-.')
plt.title('Study Hours Over Days')
plt.xlabel('Days')
plt.ylabel('Study Hours')
plt.show()
```

**Observation:** Plots study hours for each day using a dash-dot line and circle markers. Demonstrates `plt.plot()` with `marker`, `color`, and `linestyle` parameters.

---

#### Advanced Line Chart — Study Hours and Marks Trend

```python
plt.figure(figsize=(7, 4))
plt.plot(df['Days'], df['Study_Hours'], marker='*', label='Study Hours', color='green')
plt.plot(df['Days'], df['Marks'], marker='s', color='aqua', label='Marks')
plt.title('Study Hours and Marks Trend')
plt.xlabel('Days')
plt.ylabel('Value')
plt.legend()
plt.show()
```

**Observation:** Overlays two series on one figure to compare study hours against marks. Uses `plt.legend()` to differentiate series.

---

#### Bar Charts

**Basic Bar Chart:**

```python
plt.bar(df['Days'], df['Marks'], color='#FFD700', edgecolor='black', linewidth=2)
plt.title('Marks Comparison')
plt.xlabel('Days')
plt.ylabel('Marks')
plt.show()
```

**Bar Chart with Value Labels:**

```python
bars = plt.bar(df['Days'], df['Marks'], color='#800080')
for bar in bars:
    y = bar.get_height()
    plt.text(bar.get_x() + bar.get_width() / 2, y, str(y), ha='center', va='bottom')
plt.title('Marks Comparison')
plt.xlabel('Days')
plt.ylabel('Marks')
plt.grid(axis='y')
plt.show()
```

**Grouped Bar Chart:**

```python
x = np.arange(len(df['Days']))
width = 0.35
plt.bar(x - width / 2, df['Study_Hours'], width, label='Study Hours')
plt.bar(x + width / 2, df['Marks'], width, label='Marks')
plt.xticks(x, df['Days'])
plt.title('Study Hours vs Marks')
plt.legend()
plt.show()
```

---

#### Histogram — Marks Distribution

```python
plt.hist(hist_df['Marks'], bins=3, color='cyan', edgecolor='black', alpha=0.5)
plt.axvline(mean_value, color='red', linestyle='--', linewidth=2, label='Mean')
plt.title('Marks Distribution')
plt.legend()
plt.show()
```

**Observation:** A red dashed `axvline` marks the mean value for reference.

---

#### Scatter Plots

**Basic Scatter:**

```python
plt.scatter(df['Study_Hours'], df['Marks'])
plt.title('Study Hours vs Marks')
plt.show()
```

**Conditional Scatter (Result-wise):**

```python
df['Result'] = ['Fail', 'Pass', 'Fail', 'Pass', 'Pass']
colors = ['red' if r == 'Fail' else 'green' for r in df['Result']]
plt.scatter(df['Study_Hours'], df['Marks'], c=colors)
plt.title('Study Hours vs Marks (Result-wise)')
plt.show()
```

---

### 5.2 Seaborn Visualisations — Dataset 1

```python
sns.lineplot(x='Days', y='Marks', data=df1)
plt.title('Seaborn Line Plot — Marks Over Days')
plt.show()

sns.histplot(df1['Marks'], bins=3)
plt.title('Seaborn Histogram — Marks Distribution')
plt.show()
```

---

### 5.3 Matplotlib Visualisations — Dataset 2 (Sales Performance)

**Purpose:** Repeat all chart types from Section 5.1 on the larger 10-row sales dataset. Day labels are formatted as `Day(entry_number)` and rotated 45° for readability.

**Data Structure:**

```python
data2 = {
    'Day':      ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun', 'Mon', 'Tue', 'Wed'],
    'Region':   ['North', 'South', 'East', 'West', 'North', 'South', 'East', 'West', 'North', 'South'],
    'Sales':    [200, 220, 250, 270, 300, 350, 400, 280, 260, 290],
    'Profit':   [20,  25,  30,  35,  50,  60,  80,  40,  38,  45],
    'Customers':[30,  35,  40,  45,  50,  65,  80,  55,  48,  52],
    'Category': ['Food', 'Clothing', 'Electronics', 'Food', 'Clothing',
                 'Electronics', 'Food', 'Clothing', 'Electronics', 'Food']
}
```

Charts produced:

- Line chart — Sales Over Days (blue dash-dot)
- Advanced line — Sales and Profit Trend overlaid
- Bar, bar with value labels, grouped bar (Sales vs Profit)
- Histogram — Sales Distribution with mean reference line
- Scatter — Sales vs Profit (plain and category-coloured with legend patches)

---

### 5.4 Seaborn Visualisations — Dataset 2

```python
sns.lineplot(x=range(len(df2)), y='Sales', data=df2, marker='o', color='navy')
plt.title('Seaborn Line Plot — Sales Over Days (Dataset 2)')
plt.show()

sns.histplot(df2['Sales'], bins=4, color='cornflowerblue', edgecolor='black')
plt.title('Seaborn Histogram — Sales Distribution (Dataset 2)')
plt.show()

sns.scatterplot(x='Sales', y='Profit', hue='Category', data=df2, s=100)
plt.title('Seaborn Scatter Plot — Sales vs Profit by Category (Dataset 2)')
plt.show()
```

---

### 5.5 Advanced Seaborn Visualisations — Dataset 3 (Extended Sales, 42 rows)

**Dataset generated using:**

```python
np.random.seed(42)
# 42 rows with Day, Region, Category, Sales, Profit, Customers, Rating
```

| # | Chart | Function | Key Insight Shown |
|---|---|---|---|
| 1 | Pairplot | `sns.pairplot()` | All pairwise numeric relationships coloured by Category |
| 2 | Correlation Heatmap | `sns.heatmap(corr, annot=True)` | Pearson correlations between Sales, Profit, Customers, Rating |
| 3 | Violin Plot | `sns.violinplot()` | Full Sales distribution shape and quartiles per Category |
| 4 | Boxen Plot | `sns.boxenplot()` | Extended quantile view of Profit per Region |
| 5 | Strip + Swarm | `sns.stripplot()` / `sns.swarmplot()` | All individual Customer data points side-by-side |
| 6 | FacetGrid | `sns.FacetGrid(col='Category')` | Per-category Sales histograms in separate panels |
| 7 | KDE Plot | `sns.kdeplot()` | Smooth Sales density curves for all three categories |
| 8 | Countplot | `sns.countplot(hue='Category')` | Record frequency per Region split by Category |
| 9 | Barplot (aggregated) | `sns.barplot(estimator='mean')` | Mean Sales by Category and Mean Profit by Region with CI bars |
| 10 | Lineplot (styled) | `sns.lineplot(hue=, style=, markers=True)` | Average daily Sales per Category with markers and dashed lines |
| 11 | Dashboard | `plt.subplots(2, 3)` | 2×3 panel: boxplot, bar, histogram, scatter, KDE, filled line |

---

## 6. Key Learnings

### 6.1 Chart Type Selection Guide

| Chart Type | Function | Purpose |
|---|---|---|
| Line Chart | `plt.plot()` | Show trends and changes over time |
| Bar Chart | `plt.bar()` | Compare values across discrete categories |
| Histogram | `plt.hist()` | Show frequency distribution of a variable |
| Scatter Plot | `plt.scatter()` | Reveal relationships between two numeric variables |
| Seaborn Lineplot | `sns.lineplot()` | Styled line plots with statistical confidence |
| Seaborn Histplot | `sns.histplot()` | Enhanced histogram with optional KDE overlay |
| Seaborn Scatterplot | `sns.scatterplot()` | Scatter with hue/style encoding |
| Pairplot | `sns.pairplot()` | Pairwise relationships across all numeric columns |
| Heatmap | `sns.heatmap()` | Correlation matrix as colour-coded grid |
| Violin Plot | `sns.violinplot()` | Distribution shape and quartile summary |
| Boxen Plot | `sns.boxenplot()` | Extended box plot showing more quantiles |
| Strip / Swarm | `sns.stripplot()` / `sns.swarmplot()` | Individual data points by category |
| FacetGrid | `sns.FacetGrid()` | Multi-panel chart grid split by category |
| KDE Plot | `sns.kdeplot()` | Smooth probability density estimation |
| Countplot | `sns.countplot()` | Frequency count per category with hue |
| Barplot (aggregated) | `sns.barplot()` | Mean/sum per group with error bars |

---

### 6.2 Key Functions and Techniques

| Concept | Function / Property | Description |
|---|---|---|
| Multiple lines on one chart | `plt.plot()` × N | Call `plot()` multiple times before `plt.show()` |
| Figure size | `plt.figure(figsize=(w, h))` | Set width and height in inches before plotting |
| Axis labels | `plt.xlabel()` / `plt.ylabel()` | Label the x and y axes |
| Legend | `plt.legend()` | Show labelled series; requires `label=` in each plot call |
| Grid | `plt.grid(axis='y')` | Add reference lines on specified axis |
| Value labels on bars | `plt.text(x, y, str(y))` | Annotate each bar with its height value |
| Grouped bar | `x ± width/2` with `np.arange()` | Offset bars using array arithmetic |
| Mean reference line | `plt.axvline(mean, linestyle='--')` | Vertical dashed line at mean |
| Colour by condition | `c=[colors]` in `scatter()` | Pass a list of colour strings mapped to a condition |
| Hue encoding (Seaborn) | `hue='column'` | Colour-code points/lines by a categorical column |
| Subplots dashboard | `plt.subplots(rows, cols)` | Returns fig and axes array for multi-panel layout |
| Tight layout | `plt.tight_layout()` | Prevents overlapping labels in multi-chart figures |

---

### 6.3 Marker and Colour Reference

| Marker | Meaning |
|---|---|
| `'o'` | Circle ● |
| `'s'` | Square ■ |
| `'^'` | Triangle ▲ |
| `'x'` | Cross ✖ |
| `'*'` | Star ⭐ |

**Common named colours:** `'blue'`, `'red'`, `'green'`, `'black'`, `'orange'`, `'cyan'`, `'pink'`, `'coral'`, `'navy'`, `'steelblue'`

**Short forms:** `'b'` → blue, `'r'` → red, `'g'` → green, `'k'` → black

**Hex colours** are also accepted, e.g. `'#FFD700'`, `'#800080'`

---

### 6.4 Best Practices

1. Always set `plt.figure(figsize=())` for charts with many labels to prevent crowding.
2. Use `plt.tight_layout()` in all multi-chart figures to avoid overlapping axes.
3. Rotate x-axis tick labels with `rotation=45` for long or indexed day labels.
4. Always add `plt.legend()` when plotting more than one series on a single axes.
5. Use `np.random.seed()` when generating synthetic datasets for reproducibility.
6. Prefer `sns.scatterplot(hue=)` over manual colour lists for categorical colour encoding.
7. Use `FacetGrid` when comparing distributions across categories without manual subplot indexing.

---

## 7. Observations

- Higher study hours correlate positively with higher marks across all five days.
- Sales peak on Sunday (entry 7) and are lowest on Monday (entry 1) in Dataset 2.
- The pairplot on Dataset 3 shows that Profit and Customers have a moderate positive relationship with Sales.
- The correlation heatmap confirms that Rating is largely uncorrelated with the other sales metrics.
- Violin plots reveal that Electronics has a wider Sales spread than Food or Clothing.
- The FacetGrid makes it easy to compare distributions across categories without manual subplot indexing.
- KDE plots are smoother and more interpretable than histograms when comparing multiple groups.

---

## 8. Conclusion

This experiment successfully demonstrated the breadth of Python's data visualisation ecosystem across three datasets of increasing complexity. Starting with basic Matplotlib charts on a 5-row student dataset and progressing to a 42-row multi-category sales dataset with advanced Seaborn techniques, the experiment covered the complete chart vocabulary needed for exploratory data analysis.

The key takeaway is that chart selection should be driven by the question being asked: line charts for trends, bar charts for comparison, histograms and KDE plots for distributions, scatter plots for relationships, and violin or boxen plots for group-level distributional detail. Seaborn's `hue` and `style` parameters, combined with Matplotlib's subplot system, allow multiple data dimensions to be encoded in a single coherent figure.

---

## 9. References

- Matplotlib Documentation: https://matplotlib.org/stable/contents.html
- Seaborn Documentation: https://seaborn.pydata.org/
- Pandas Documentation: https://pandas.pydata.org/docs/
- NumPy Documentation: https://numpy.org/doc/
- Matplotlib Pyplot Tutorial: https://matplotlib.org/stable/tutorials/introductory/pyplot.html
- Seaborn Tutorial — Statistical Data Visualization: https://seaborn.pydata.org/tutorial.html
