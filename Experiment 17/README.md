# 📈 Statistical and Specialized Data Visualization — Experiment 17

---

## 👤 Student Details

| Field | Details |
|---|---|
| **Name** | Krish Joshi |
| **PRN** | 25070123064 |
| **Class** | EnTC A3 |
| **Batch** | 2025–2029 |
| **Experiment No.** | 17 |
| **Date** | 8 April 2026 |

---

## 📌 Overview

This experiment demonstrates statistical and specialized data visualization techniques using Python's Matplotlib and Seaborn libraries. It progresses from compact five-row categorical data for foundational chart types to a realistic hundred-row loan applicant dataset for advanced exploratory data analysis. The self-learning section extends into GroupBy aggregations, feature engineering, pivot tables, cross-tabulation, ranking, and fifteen distinct visualization techniques.

---

## 🎯 Objectives

- Create area plots, pie charts, and donut charts for part-to-whole and trend representation
- Use boxplots for outlier detection and distribution spread analysis
- Build heatmaps to visualize correlations between numeric variables
- Create bubble plots to encode a third numeric dimension via marker size
- Apply advanced Seaborn techniques including violin, swarm, KDE, joint, and pair plots
- Perform feature engineering and GroupBy aggregations using pandas
- Construct multi-panel dashboards using subplot layouts
- Compute and interpret descriptive statistics including skewness and kurtosis

---

## 🛠️ Tech Stack

| Library | Purpose |
|---|---|
| `matplotlib` | Core plotting engine for all chart types |
| `seaborn` | Statistical visualization with built-in aesthetics |
| `pandas` | Data loading, cleaning, and aggregation |
| `numpy` | Numerical operations and synthetic data generation |

---

## 🗂️ Datasets Used

**Dataset 1 — Categorical (5 rows):** Contains Category labels A through E with Values, Sales, and Profit columns. Generated with a fixed random seed for reproducibility. Used for area plots, pie and donut charts, boxplots, heatmaps, and bubble plots.

**Dataset 2 — Loan Applicants (100 rows):** Contains Customer ID, Age, Income, Loan Amount, Credit Score, and a derived Loan Status column. Loan Status is assigned as Approved for credit scores above 600 and Rejected otherwise, creating a clean binary classification that drives all subsequent analysis.

---

## 🔬 Methodology

### Part A — Core Charts (Dataset 1)

#### 1. Area Plot
The area beneath a line is filled with color using Matplotlib's `fill_between` function. A single-series area plot shows the Values column across five categories. An overlaid version then stacks a Sales series and a Profit series with different colors and partial transparency, allowing visual comparison of both trends simultaneously.

#### 2. Pie Chart
Each category's share of the total is displayed as a proportional slice with percentage labels formatted to two decimal places. Category A contributes zero and does not produce a visible slice. Category D dominates with the highest value (90), followed by B (70) and E (60).

#### 3. Donut Chart
A donut chart is created by drawing a pie chart and then overlaying a filled circle at the center to remove the middle section. This is achieved by retrieving the current figure's axes object and adding the circle as an artist. The result is aesthetically cleaner than a standard pie chart for dashboards.

#### 4. Boxplot
A Seaborn boxplot visualizes the spread of the Values column, showing the median, the interquartile range (IQR) as the box, whiskers extending to 1.5× the IQR, and any data points beyond that as individual outlier markers. This chart is used for quick anomaly detection.

#### 5. Heatmap
Two heatmaps are produced. The first correlates only Sales and Profit using a coolwarm colormap where positive correlations appear red and negative correlations appear blue. The second extends this to include Values as a third variable. Annotated cell values show the Pearson correlation coefficient directly on the grid.

#### 6. Bubble Plot
A bubble plot encodes a third variable as marker size, layering three dimensions of information onto a two-dimensional scatter canvas. Matplotlib's scatter function uses the `s` parameter for raw size, while Seaborn's scatterplot adds `hue` encoding so the same variable is also represented by color through a continuous palette.

---

### Part B — Core Charts (Dataset 2 — Loan Applicants)

#### Boxplot — Loan Amount Distribution
Loan amounts are approximately uniformly distributed between 5,000 and 50,000 with no extreme outliers, which is expected from the uniform random generation method used. The boxplot confirms symmetry around the midpoint.

#### Histogram — Credit Score Distribution
With six bins across the 300 to 900 range, each bin covers 100 credit score points. The distribution appears roughly flat and uniform, consistent with the random generation process. No natural peaks or skew are visible.

#### Bubble Plot — Income vs Loan Amount
Both marker size and marker color encode Credit Score simultaneously. A colorbar legend makes the color scale readable. Higher credit scores appear both larger and lighter (yellow in the viridis palette), giving two redundant visual cues that reinforce each other.

#### Correlation Heatmap — All Numeric Columns
All four numeric columns — Age, Income, Loan Amount, and Credit Score — show correlations close to zero. This confirms the variables were generated independently and serves as an important baseline check that validates the synthetic data structure.

---

### Part C — Self-Learning Advanced Analysis (Dataset 2)

#### 1. GroupBy Aggregations
The dataset is grouped by Loan Status and multiple aggregate functions (mean, median, standard deviation, min, max, count) are applied simultaneously to multiple columns. The key finding is that Approved and Rejected customers have nearly identical average incomes ($54,959 vs $55,629), confirming that income alone does not determine approval — credit score is the decisive variable.

#### 2. Feature Engineering
Four new columns are derived from existing data. The Debt-to-Income (DTI) ratio divides Loan Amount by Income and multiplies by 100. Age Group bins customers into four labeled segments (Young, Middle, Senior, Mature) using pandas cut. Credit Category applies five credit quality tiers using cut with defined boundaries. Income Level creates a binary label above and below the median income using NumPy's where function. These engineered features enable far richer segmentation than the raw columns allow.

#### 3. Pivot Tables
Two pivot tables summarize the dataset across two categorical dimensions simultaneously. The first shows mean Loan Amount grouped by Age Group and Loan Status, revealing that Senior applicants (41–50) who were approved requested the highest average loan amounts at approximately $37,853. The second shows mean, min, max, and count of Credit Score by Income Level.

#### 4. Cross-Tabulation
A frequency cross-tabulation counts the number of Approved and Rejected cases for each Credit Category. A normalized version converts counts to row percentages. The result reveals a perfect binary threshold: all customers with credit scores below 600 are Rejected (100%), and all customers above 600 are Approved (100%). No borderline or ambiguous cases exist in this synthetic dataset.

#### 5. Ranking
Credit Score, Income, and DTI are each ranked using dense ranking, which assigns the same rank to ties without creating gaps in the sequence. Lower DTI ranks best since a smaller debt burden is more favorable. The top-10 customers by each rank are extracted efficiently using the `nsmallest` function.

#### 6. Pair Plot
All four numeric variables are plotted against each other in a grid, colored by Loan Status. Diagonal panels show kernel density estimates for each variable. The Credit Score column produces the only clear visual separation between the two groups. All other pairwise combinations show complete overlap, confirming that credit score is the sole determinant of approval in this dataset.

#### 7. Violin Plot
Side-by-side violins show the full distribution shape and quartile markers for Credit Score and Income, grouped by Loan Status. The Credit Score violins are completely non-overlapping — a hard separation at the 600 threshold — while the Income violins are nearly identical in shape and position, providing further evidence that income does not influence approval.

#### 8. Joint Plot
A bivariate joint plot with a regression line and confidence band examines the relationship between Income and Loan Amount. Marginal histograms appear on both axes. The near-flat regression line confirms the absence of any meaningful correlation between these two variables.

#### 9. Subplots Dashboard — 2×2 Panel
A four-panel dashboard assembles: a Credit Score KDE plot by Loan Status (top-left), an Income histogram with a red dashed mean reference line (top-right), a Loan Amount boxplot grouped by Age Group (bottom-left), and a Credit Score vs Income scatter colored by Loan Amount using the plasma colormap (bottom-right). The dashboard is saved as a PNG file before rendering.

#### 10. Statistical Summary
Descriptive statistics are computed for all numeric columns. All four variables show negative kurtosis values, confirming platykurtic (flatter than normal) distributions with lighter tails — consistent with uniform random generation. Skewness values are all close to zero, indicating approximately symmetric distributions. The overall loan approval rate is 47%.

#### 11. Countplot with Hue
Two countplots display the frequency of Approved vs Rejected cases segmented by Age Group and Credit Category. Young applicants (20–30) have the highest approval count. The Credit Category countplot visually confirms the hard approval threshold — no approvals exist below 600 and no rejections exist above it.

#### 12. Stacked Bar Chart
Loan Status counts are grouped by Age Group and plotted as a stacked horizontal bar chart. Bar labels are placed inside each segment using the bar_label function. Approval rate declines with age in this dataset — Young applicants have the highest approval share while Senior applicants have the lowest.

#### 13. KDE Plot
A dual KDE plot shows Credit Score density by Loan Status with a vertical dashed line at the 600 threshold that bisects the two curves cleanly. A second panel shows Income density by Age Group, where all four curves largely overlap — confirming no income bias across age segments.

#### 14. Swarm Plot
Every individual data point is plotted as a non-overlapping marker, colored by Age Group, with Loan Status on the x-axis. A horizontal dashed line at Credit Score 600 makes the approval boundary immediately visible as a hard cutoff. The legend is placed outside the plot area to avoid obscuring any data points.

#### 15. Summary Statistics Table
A final aggregated table shows Count, Average Credit Score, Average Income, Average Loan Amount, and Average DTI side by side for Approved and Rejected customers. Approved customers average a credit score of 741.77 while Rejected customers average 453.06, with all other metrics nearly identical between groups.

---

## 📊 Key Insights

- Credit score is the sole determinant of loan approval — all customers above 600 are approved, all below are rejected, with no exceptions
- Approved and Rejected customers have nearly identical average incomes and DTI ratios, confirming income does not affect the outcome
- All four numeric variables exhibit negative kurtosis (platykurtic), consistent with uniform random generation
- Young applicants (20–30) have the highest approval count at 19 out of 33 in that group
- Senior applicants (41–50) have the lowest approval rate at 8 out of 25
- The bubble plot on Dataset 1 shows no clear relationship between Sales and Profit, consistent with independent random generation

---

## ▶️ How to Run

1. **Clone the repository** — Download or clone this repo to your local machine.
2. **Install dependencies** — Install Matplotlib, Seaborn, Pandas, and NumPy using pip.
3. **Launch the notebook** — Open the experiment notebook in Jupyter Notebook, JupyterLab, or Google Colab.
4. **Save dashboard outputs** — The 2×2 subplot dashboard is automatically saved as a PNG file using `savefig` before the figure renders.

---

## 🔑 Key Learnings

### Chart Selection Principles
The right chart depends entirely on what question is being asked. KDE plots and violin plots work best for comparing distributions across groups. Joint plots reveal bivariate relationships with marginal context. Swarm plots preserve every individual data point without overlap. Stacked bar charts compare both total counts and internal composition across categories.

### Important Pandas Techniques
The `pd.cut` function is preferred over manual conditional chains for ordered categorical binning. `pd.crosstab` with `normalize='index'` converts raw counts to row-wise percentages for fair comparison across groups of different sizes. Dense ranking via `rank(method='dense')` avoids gaps in the rank sequence when ties occur. `nsmallest` efficiently retrieves top-N rows without sorting the entire dataframe.

### Technical Notes
Always use a fixed random seed before generating synthetic datasets to ensure reproducibility across runs. Save multi-panel figures with `savefig` before calling `show`, as `show` clears the figure from memory. Use `tight_layout` in all multi-panel figures to prevent axis label overlap. Use `bbox_to_anchor` to position legends outside the plot area when data points would be obscured.

---

## 📄 Conclusion

This experiment successfully demonstrated a broad range of statistical and specialized visualization techniques across two datasets of increasing complexity. Foundational chart types on the five-row categorical dataset built intuition for encoding, color, and layout fundamentals. The hundred-row loan applicant dataset then enabled meaningful statistical analysis, where GroupBy, feature engineering, pivot tables, cross-tabulation, and fifteen visualization techniques worked together to produce a complete exploratory data analysis.

The central insight — that credit score above 600 perfectly determines loan approval, while income plays no role — emerged not from a single chart but from the cumulative evidence of heatmaps, violins, KDE plots, crosstabs, and swarm plots all pointing to the same conclusion. This illustrates the core principle of EDA: multiple views of the same data, each asking a slightly different question, build toward understanding that no single visualization could achieve alone.

---

## 🔗 References

- Matplotlib Documentation: https://matplotlib.org/stable/contents.html
- Seaborn Documentation: https://seaborn.pydata.org/
- Pandas Documentation: https://pandas.pydata.org/docs/
- NumPy Documentation: https://numpy.org/doc/
- Pandas GroupBy Guide: https://pandas.pydata.org/pandas-docs/stable/user_guide/groupby.html
- Seaborn Tutorial: https://seaborn.pydata.org/tutorial.html

---

<div align="center">
   <strong>Krish Joshi</strong> | EnTC A3 | PRN: 25070123064 | Batch 2025–2029
</div>
