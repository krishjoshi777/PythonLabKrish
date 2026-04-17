# 📉 Basic Charts and Visual Encoding — Experiment 16

---

## 👤 Student Details

| Field | Details |
|---|---|
| **Name** | Krish Joshi |
| **PRN** | 25070123064 |
| **Class** | EnTC A3 |
| **Batch** | 2025–2029 |
| **Experiment No.** | 16 |
| **Date** | 8 April 2026 |

---

## 📌 Overview

This experiment establishes the foundational vocabulary of Python data visualization using Matplotlib and Seaborn. Working across three datasets of increasing size and complexity — from a five-row student performance table to a forty-two-row multi-category sales dataset — the experiment covers every essential chart type used in exploratory data analysis, from simple line trends to advanced Seaborn violin and FacetGrid plots.

---

## 🎯 Objectives

- Create line charts to visualize trends over time or across ordered categories
- Build bar charts for categorical comparisons including labeled and grouped variants
- Plot histograms to understand value frequency distributions
- Use scatter plots to explore relationships between two numeric variables
- Apply color encoding and conditional formatting to communicate additional data dimensions
- Use advanced Seaborn charts including pairplot, heatmap, violin, KDE, and FacetGrid
- Compose multi-panel dashboards using subplot layouts

---

## 🛠️ Tech Stack

| Library | Purpose |
|---|---|
| `matplotlib` | Core plotting engine for all chart types |
| `seaborn` | High-level statistical visualization built on Matplotlib |
| `pandas` | Data structuring and DataFrame operations |
| `numpy` | Numerical operations and synthetic data generation |

---

## 🗂️ Datasets Used

**Dataset 1 — Student Performance (5 rows):** Records study hours, marks, attendance, sleep hours, and assignments completed across five days of the week. Used for all foundational Matplotlib and Seaborn chart types.

**Dataset 2 — Sales Performance (10 rows):** Contains daily sales, profit, customer count, region, and product category across ten trading days. Used to repeat all chart types from Dataset 1 on a larger and more varied dataset with four regions and three categories.

**Dataset 3 — Extended Sales Data (42 rows):** A randomly generated dataset with day, region, category, sales, profit, customer count, and rating columns. Used exclusively for advanced Seaborn charts including pairplot, heatmap, violin, boxen, strip, swarm, FacetGrid, KDE, and the full multi-panel dashboard.

---

## 🔬 Methodology

### Part A — Matplotlib Visualizations (Dataset 1)

#### 1. Line Chart — Study Hours Over Days
A single line is plotted across five weekdays using a dash-dot line style with circle markers. This chart introduces the core `plot` function and its parameters for controlling line style, marker shape, and color. Study hours increase through Thursday before dropping slightly on Friday.

#### 2. Advanced Line Chart — Study Hours and Marks Trend
Two series — Study Hours and Marks — are plotted on the same axes using different marker shapes and colors. A legend differentiates the two series. Overlaying related trends on a single figure is a core technique for comparing parallel time series without visual confusion.

#### 3. Basic Bar Chart
Marks for each day of the week are displayed as vertical bars with a gold fill and black edge. This introduces `plt.bar` with the `color`, `edgecolor`, and `linewidth` parameters.

#### 4. Bar Chart with Value Labels
The same bar chart is enhanced by annotating each bar at its top with the precise numeric value. This is achieved by iterating over each bar object, retrieving its height, and placing a text label at the appropriate x and y position.

#### 5. Grouped Bar Chart — Study Hours vs Marks
Two bars per day are placed side by side by offsetting their x positions by half the bar width in opposite directions using NumPy array arithmetic. A legend identifies each group. This layout is effective for direct side-by-side comparison of two related metrics per category.

#### 6. Histogram — Marks Distribution
Marks data is binned into three equal-width intervals. A red dashed vertical line is placed at the mean value using `axvline`, providing a reference point for skew assessment. The legend labels this line clearly.

#### 7. Basic Scatter Plot — Study Hours vs Marks
Each data point is plotted as a circle with study hours on the x-axis and marks on the y-axis. A positive trend is visible — students who study more score higher.

#### 8. Conditional Scatter Plot — Result-wise Coloring
A Result column is derived by labeling each student as Pass or Fail. A list of color strings is constructed based on this condition and passed as the `c` parameter to the scatter function. Failing students appear in red and passing students in green, adding a third categorical dimension without adding a new axis.

---

### Part B — Seaborn Visualizations (Dataset 1)
Seaborn's `lineplot` and `histplot` functions are applied to the same student dataset. These produce more polished and aesthetically consistent outputs compared to their Matplotlib equivalents, with automatic theme support from `sns.set_style`.

---

### Part C — Matplotlib Visualizations (Dataset 2)

All eight chart types from Part A are repeated on the ten-row sales dataset. Day labels are formatted as indexed entries and rotated 45 degrees for readability. The conditional scatter applies category-based color encoding — Food, Clothing, and Electronics each receive a distinct color, with a manual legend built from color patches.

Key observations on Dataset 2:
- Sales peak on Sunday (Day 7) at 400 and are lowest on Monday (Day 1) at 200
- The histogram reveals that most daily sales cluster below 300
- The scatter of Sales vs Profit shows a positive relationship — higher sales generally produce higher profits

---

### Part D — Seaborn Visualizations (Dataset 2)
Seaborn's `lineplot`, `histplot`, and `scatterplot` are applied to the sales dataset. The scatterplot uses the `hue` parameter to color-code each point by Category and sets marker size to 100 for improved visibility. This demonstrates how Seaborn's declarative `hue` encoding is more concise and consistent than manually constructing color lists in Matplotlib.

---

### Part E — Advanced Seaborn Visualizations (Dataset 3)

#### 1. Pairplot
All pairwise combinations of Sales, Profit, Customers, and Rating are plotted in a grid colored by Category. Diagonal panels display kernel density estimates for each individual variable. Profit and Customers show a moderate positive relationship with Sales. Rating is largely uncorrelated with all other variables.

#### 2. Correlation Heatmap
The Pearson correlation matrix for all four numeric variables is rendered as an annotated color grid using the coolwarm palette. This confirms the pairplot findings: Rating stands apart from the rest with near-zero correlations throughout.

#### 3. Violin Plot — Sales by Category
Full distribution shapes for Sales are shown per category using violin plots, which combine a density estimate with quartile markers inside. Electronics shows the widest Sales spread, while Food has the most compact distribution.

#### 4. Boxen Plot — Profit by Region
A boxen (letter-value) plot extends the traditional boxplot by displaying more quantile levels, offering a richer picture of the Profit distribution for each region. This is particularly useful for identifying multi-modal distributions or unusual tail shapes.

#### 5. Strip and Swarm Plots — Customers by Region
Strip plots place all individual Customer data points along a category axis with random jitter to reduce overlap. Swarm plots remove jitter entirely, spacing points algorithmically so none overlap. Displaying both side by side illustrates the trade-off between distribution density and point legibility.

#### 6. FacetGrid — Sales Histograms by Category
A FacetGrid creates separate histogram panels for each Category (Food, Clothing, Electronics) side by side without requiring manual subplot indexing. This makes per-category distribution comparison straightforward and scalable.

#### 7. KDE Plot — Sales Density by Category
Smooth kernel density curves for all three categories are overlaid on a single axes. KDE plots are more interpretable than histograms when comparing multiple groups because they eliminate binwidth sensitivity and produce continuous, comparable curves.

#### 8. Countplot — Record Frequency by Region and Category
A countplot shows how many records exist per Region, with bars split by Category using the `hue` parameter. This reveals how evenly the dataset is distributed across regions and which categories dominate each region.

#### 9. Barplot — Mean Sales and Mean Profit
Two aggregated bar plots show mean Sales by Category and mean Profit by Region with confidence interval error bars generated automatically by Seaborn. This provides a statistical summary alongside the raw distribution charts.

#### 10. Styled Lineplot — Daily Sales by Category
Sales trends over time are shown per Category using different line styles and markers via the `hue` and `style` parameters. This combination of color and style makes the three category lines distinguishable even in monochrome printouts.

#### 11. Dashboard — 2×3 Subplot Panel
A six-panel dashboard assembles: a boxplot, a bar chart, a histogram, a scatter plot with color encoding, a KDE distribution, and a filled area chart — all in one coherent layout. The `tight_layout` function prevents overlapping axis labels across panels.

---

## 📊 Key Insights

- Higher study hours consistently correlate with higher marks across all five days in Dataset 1
- Sales peak on Sunday and are lowest on Monday in Dataset 2
- The pairplot on Dataset 3 shows Profit and Customers have a moderate positive relationship with Sales
- Rating is almost completely uncorrelated with all other sales metrics
- Electronics shows the widest Sales distribution spread across all three categories
- KDE plots are significantly more interpretable than histograms when comparing multiple groups on the same axes
- FacetGrid enables per-category distribution comparison without requiring manual subplot configuration

---

## ▶️ How to Run

1. **Clone the repository** — Download or clone this repo to your local machine.
2. **Install dependencies** — Install Matplotlib, Seaborn, Pandas, and NumPy using pip.
3. **Launch the notebook** — Open the experiment notebook in Jupyter Notebook, JupyterLab, or Google Colab for a zero-setup experience.
4. **Reproduce results** — All synthetic datasets use fixed random seeds, so every chart will render identically on any machine.

---

## 🔑 Key Learnings

### Chart Type Selection Guide

| Question Being Asked | Recommended Chart |
|---|---|
| How does a value change over time? | Line Chart |
| How do categories compare? | Bar Chart |
| How is a variable distributed? | Histogram or KDE Plot |
| Is there a relationship between two numeric variables? | Scatter Plot |
| How do distributions compare across groups? | Violin or KDE Plot |
| What are all pairwise numeric relationships? | Pairplot |
| How are variables correlated? | Heatmap |
| What does the distribution look like for each category separately? | FacetGrid |
| How many records are in each category? | Countplot |
| What is the average per group with uncertainty? | Seaborn Barplot |

### Matplotlib vs Seaborn
Matplotlib provides full control over every element of a chart but requires more explicit code for aesthetics and statistical features. Seaborn's `hue` and `style` parameters handle categorical color and line-style encoding in a single declarative statement. For groupwise comparisons, Seaborn is almost always more concise. For custom layouts, annotations, and absolute control, Matplotlib is essential.

### Technical Notes
Always set the figure size with `figsize` before creating charts with many labels to prevent crowding. Rotate x-axis tick labels by 45 degrees when labels are long or numerous. Use `tight_layout` whenever multiple panels share a figure. Always call `savefig` before `show` in dashboards — `show` clears the figure from memory and the file will be empty if saved afterward.

---

## 📄 Conclusion

This experiment successfully established the complete foundational chart vocabulary of Python data visualization. Working through three datasets of increasing complexity — five-row student data, ten-row sales data, and forty-two-row extended sales data — every core chart type was introduced, practiced, and then revisited with Seaborn's more powerful API.

The key takeaway is that chart selection must be driven by the analytical question being asked, not by habit or aesthetics. Line charts for trends, bar charts for comparisons, histograms and KDE plots for distributions, scatter plots for relationships, and violin or boxen plots for group-level distributional detail each serve distinct purposes. Seaborn's `hue`, `style`, and `FacetGrid` parameters, combined with Matplotlib's subplot system, allow multiple data dimensions to be encoded in a single coherent and readable figure.

---

## 🔗 References

- Matplotlib Documentation: https://matplotlib.org/stable/contents.html
- Seaborn Documentation: https://seaborn.pydata.org/
- Pandas Documentation: https://pandas.pydata.org/docs/
- NumPy Documentation: https://numpy.org/doc/
- Matplotlib Pyplot Tutorial: https://matplotlib.org/stable/tutorials/introductory/pyplot.html
- Seaborn Tutorial: https://seaborn.pydata.org/tutorial.html

---

<div align="center">
  <strong>Krish Joshi</strong> | EnTC A3 | PRN: 25070123064 | Batch 2025–2029
</div>
