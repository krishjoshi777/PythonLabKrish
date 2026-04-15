# Lab Experiment Journal: Exploring Statistical and Specialized Data Visualization Techniques

---

## Experiment Details

| Field | Value |
|---|---|
| **Experiment Title** | Exploring Statistical and Specialized Data Visualization Techniques |
| **Date** | 2026-04-08 |
| **Student Name** | Krish Joshi |
| **PRN** | 25070123064 |
| **Batch** | EnTC A3 |
| **Experiment No.** | 17 |
| **Programming Language** | Python 3.x |
| **Libraries Used** | matplotlib, seaborn, pandas, numpy |

---

## 1. Objective

To understand and implement statistical and specialized data visualization techniques in Python using Matplotlib and Seaborn, including:

- Creating area plots, pie charts, and donut charts for part-to-whole and trend representation
- Using boxplots for outlier detection and distribution analysis
- Building heatmaps to visualize correlations between variables
- Creating bubble plots to encode a third dimension via marker size
- Applying advanced Seaborn techniques (violin, swarm, KDE, joint, pair plots)
- Performing feature engineering and GroupBy aggregations with pandas
- Constructing multi-panel dashboards using `plt.subplots()`
- Computing and interpreting descriptive statistics including skewness and kurtosis

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
| **Dataset 1** | Category, Values, Sales, Profit | 5 rows; synthetic categorical data generated with `np.random.seed(10000000)`; used for area plots, pie/donut charts, boxplot, heatmap, bubble plot |
| **Dataset 2** | Customer_ID, Age, Income, Loan_Amount, Credit_Score, Loan_Status | 100 rows; synthetic loan applicant data generated with `np.random.seed(7)`; Loan_Status derived from Credit_Score > 600; used for all advanced analysis |

---

## 4. Experiment Sections

| No. | Section | Dataset | Charts / Techniques |
|---|---|---|---|
| 4.1 | Core Charts — Dataset 1 | Categorical (5 rows) | Area plot, overlaid area plot, pie chart, donut chart, boxplot, heatmap (2×), bubble plot (2×) |
| 4.2 | Core Charts — Dataset 2 | Loan Applicants (100 rows) | Boxplot, histogram, bubble plot, correlation heatmap |
| 4.3 | Self-Learning — Advanced Analysis | Loan Applicants (100 rows) | GroupBy, feature engineering, pivot tables, crosstab, ranking, pair plot, violin, joint plot, subplots dashboard, statistical summary, countplot, stacked bar, KDE, swarm plot, summary table |

---

## 5. Experiment Sections (Detailed)

### 5.1 Core Charts — Dataset 1

**Data Structure:**

```python
np.random.seed(10000000)
df = pd.DataFrame({
    'Category': ['A', 'B', 'C', 'D', 'E'],
    'Values':   [0, 70, 30, 90, 60],
    'Sales':    np.random.randint(100, 500, 5),
    'Profit':   np.random.randint(10, 100, 5)
})
```

---

#### 1. Area Plot

```python
plt.figure()
plt.fill_between(df['Category'], df['Values'], color='green', alpha=0.25)
plt.xlabel('Category')
plt.title("Area Plot")
plt.ylabel('Values')
plt.show()
```

**Observation:** `plt.fill_between()` shades the area under a line. The `alpha` parameter controls transparency, allowing overlapping areas to remain visible.

---

#### Overlaid Area Plot — Sales and Profit

```python
sns.set_style("whitegrid")
plt.figure(figsize=(7, 4))
plt.fill_between(df['Category'], df['Sales'],  color='green',  alpha=0.5, label='Sales')
plt.fill_between(df['Category'], df['Profit'], color='orange', alpha=0.5, label='Profit')
plt.xlabel('Category')
plt.title("Sales and Profit Area Plot")
plt.ylabel('Values')
plt.legend()
plt.show()
```

**Observation:** Overlaying two `fill_between()` calls allows direct visual comparison of two series. `sns.set_style("whitegrid")` applies a clean background grid.

---

#### 2. Pie Chart

```python
plt.figure()
plt.pie(df['Values'], labels=df['Category'], autopct='%1.2f%%')
plt.title("Pie Chart")
plt.show()
```

**Observation:** `autopct='%1.2f%%'` formats percentage labels to two decimal places. Note: the zero value for category A contributes 0% and may not render a visible slice.

---

#### 3. Donut Chart

```python
plt.figure()
plt.pie(df['Values'], labels=df['Category'], autopct='%1.2f%%')
centre_circle = plt.Circle((0, 0), 0.50, fc='c')
fig = plt.gcf()
fig.gca().add_artist(centre_circle)
plt.title("Donut Chart")
plt.show()
```

**Observation:** A donut chart is a pie chart with a `plt.Circle` patch added at the centre. `plt.gcf()` and `fig.gca()` retrieve the current figure and axes to attach the artist.

---

#### 4. Boxplot — Outlier Detection

```python
plt.figure()
sns.boxplot(x=df['Values'])
plt.title("Boxplot of Sales")
plt.show()
```

**Observation:** Boxplots display the median, IQR (interquartile range), and any outliers beyond 1.5×IQR as individual points. Useful for quickly spotting anomalies.

---

#### 5. Heatmap — Correlation

```python
# Two-column heatmap
corr = df[['Sales', 'Profit']].corr()
sns.heatmap(corr, annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap")
plt.show()

# Three-column heatmap
corr = df[['Values', 'Sales', 'Profit']].corr()
plt.figure(figsize=(5, 4))
sns.heatmap(corr, annot=True)
plt.title("Correlation Heatmap")
plt.show()
```

**Observation:** `annot=True` prints the correlation coefficient inside each cell. `cmap='coolwarm'` maps positive correlations to red and negative to blue.

---

#### Bubble Plot

```python
# Matplotlib
plt.scatter(df['Sales'], df['Profit'], s=df['Values'] * 10)
plt.title("Bubble Plot")
plt.xlabel("Sales")
plt.ylabel("Profit")
plt.show()

# Seaborn
plt.figure(figsize=(6, 4))
sns.scatterplot(x='Sales', y='Profit', size='Values', hue='Values',
                data=df, sizes=(50, 300), palette='viridis')
plt.title("Bubble Plot using Seaborn")
plt.show()
```

**Observation:** Bubble plots encode a third variable (Values) as marker size via `s=` in Matplotlib or `size=` in Seaborn. Seaborn's `hue=` additionally encodes the same variable as colour.

---

### 5.2 Core Charts — Dataset 2 (Loan Applicant Data)

**Data Structure:**

```python
np.random.seed(7)
n = 100
df = pd.DataFrame({
    'Customer_ID':  range(1, n + 1),
    'Age':          np.random.randint(20, 60, n),
    'Income':       np.random.randint(20000, 100000, n),
    'Loan_Amount':  np.random.randint(5000, 50000, n),
    'Credit_Score': np.random.randint(300, 900, n)
})
df['Loan_Status'] = np.where(df['Credit_Score'] > 600, 'Approved', 'Rejected')
```

---

#### Boxplot — Loan Amount Distribution

```python
plt.boxplot(df['Loan_Amount'])
plt.title("Loan Amount Distribution (Boxplot)")
plt.ylabel("Loan Amount")
plt.show()
```

**Observation:** The loan amounts are approximately uniformly distributed between 5,000 and 50,000 with no extreme outliers, as expected from `randint`.

---

#### Histogram — Credit Score Distribution

```python
plt.hist(df['Credit_Score'], bins=6, color='skyblue', edgecolor='black')
plt.title("Credit Score Distribution")
plt.xlabel("Credit Score")
plt.ylabel("Frequency")
plt.show()
```

**Observation:** With 6 bins across the 300–900 range, each bin covers 100 points. The distribution appears roughly uniform, reflecting the random generation.

---

#### Bubble Plot — Income vs Loan Amount

```python
plt.scatter(df['Income'], df['Loan_Amount'],
            s=df['Credit_Score'] / 2,
            c=df['Credit_Score'],
            cmap='viridis',
            alpha=0.6)
plt.colorbar(label='Credit Score')
plt.title("Bubble Plot (Income vs Loan)")
plt.xlabel("Income")
plt.ylabel("Loan Amount")
plt.show()
```

**Observation:** Both size and colour encode Credit Score simultaneously. `plt.colorbar()` adds a colour scale legend. Higher credit scores appear larger and lighter (yellow in viridis).

---

#### Correlation Heatmap — All Numeric Columns

```python
corr = df[['Age', 'Income', 'Loan_Amount', 'Credit_Score']].corr()
sns.heatmap(corr, annot=True, cmap='coolwarm')
plt.title("Correlation Matrix")
plt.show()
```

**Observation:** All correlations are close to zero, confirming the variables were generated independently. This is an important baseline check in real EDA.

---

### 5.3 Self-Learning — Advanced Analysis (Dataset 2)

#### 1. GroupBy Aggregations

GroupBy splits data into groups, applies aggregate functions, and combines the results — essential for categorical analysis.

```python
loan_analysis = df.groupby('Loan_Status').agg({
    'Income':       ['mean', 'median', 'std'],
    'Loan_Amount':  ['mean', 'min', 'max'],
    'Credit_Score': ['mean', 'min', 'max'],
    'Age':          'mean'
}).round(2)

print(df['Loan_Status'].value_counts())
```

**Key Output:**

| Loan_Status | Avg Credit Score | Avg Income | Count |
|---|---|---|---|
| Approved | 741.77 | 54,959 | 47 |
| Rejected | 453.06 | 55,629 | 53 |

**Insight:** Approved and rejected customers have nearly identical average incomes, confirming that credit score (not income) drives approval.

---

#### 2. Feature Engineering

```python
df['DTI'] = (df['Loan_Amount'] / df['Income'] * 100).round(2)

df['Age_Group'] = pd.cut(df['Age'],
                         bins=[0, 30, 40, 50, 60],
                         labels=['Young (20-30)', 'Middle (31-40)', 'Senior (41-50)', 'Mature (51-60)'])

df['Credit_Category'] = pd.cut(df['Credit_Score'],
                                bins=[300, 500, 600, 700, 850, 900],
                                labels=['Poor (300-500)', 'Fair (501-600)', 'Good (601-700)',
                                        'Very Good (701-850)', 'Excellent (851-900)'])

df['Income_Level'] = np.where(df['Income'] >= df['Income'].median(), 'High Income', 'Low Income')
```

| New Feature | Method | Purpose |
|---|---|---|
| DTI | Loan / Income × 100 | Debt-to-Income ratio; lower is healthier |
| Age_Group | `pd.cut()` with 4 bins | Demographic segmentation |
| Credit_Category | `pd.cut()` with 5 bins | Credit quality tiering |
| Income_Level | `np.where()` vs median | Binary income classification |

**Insight:** DTI ratio helps assess borrower risk. `pd.cut()` is preferred over manual conditions for ordered categorical binning.

---

#### 3. Pivot Tables

```python
pivot_loan = pd.pivot_table(df,
                             values='Loan_Amount',
                             index='Age_Group',
                             columns='Loan_Status',
                             aggfunc='mean').round(2)

pivot_credit = pd.pivot_table(df,
                               values='Credit_Score',
                               index='Income_Level',
                               aggfunc=['mean', 'min', 'max', 'count']).round(2)
```

**Insight:** Pivot tables reveal multi-dimensional patterns — Senior applicants (41–50) who were approved had the highest average loan amounts at $37,853.

---

#### 4. Cross-Tabulation (Crosstab)

```python
crosstab_result = pd.crosstab(df['Credit_Category'], df['Loan_Status'], margins=True)

# Normalized (row percentages)
crosstab_norm = pd.crosstab(df['Credit_Category'], df['Loan_Status'],
                             normalize='index').round(3) * 100
```

**Key Output:**

| Credit Category | Approved | Rejected |
|---|---|---|
| Poor (300–500) | 0% | 100% |
| Fair (501–600) | 0% | 100% |
| Good (601–700) | 100% | 0% |
| Very Good (701–850) | 100% | 0% |
| Excellent (851–900) | 100% | 0% |

**Insight:** The credit threshold of 600 creates a perfect binary split — no borderline cases exist in this synthetic dataset.

---

#### 5. Ranking

```python
df['Credit_Rank'] = df['Credit_Score'].rank(method='dense', ascending=False)
df['Income_Rank'] = df['Income'].rank(method='dense', ascending=False)
df['DTI_Rank']    = df['DTI'].rank(method='dense', ascending=True)  # Lower DTI is better

top_credit = df.nsmallest(10, 'Credit_Rank')[['Customer_ID', 'Credit_Score', 'Credit_Rank', 'Loan_Status']]
top_income = df.nsmallest(10, 'Income_Rank')[['Customer_ID', 'Income', 'Income_Rank', 'Loan_Amount']]
```

**Insight:** `method='dense'` assigns the same rank to ties without gaps in the ranking sequence. `nsmallest()` efficiently retrieves top-N rows by rank.

---

#### 6. Pair Plot

```python
sns.pairplot(df[['Age', 'Income', 'Loan_Amount', 'Credit_Score', 'Loan_Status']],
             hue='Loan_Status',
             diag_kind='kde',
             corner=True,
             palette='Set1')
plt.suptitle('Pair Plot: Numeric Variables by Loan Status', y=1.02)
plt.show()
```

**Insight:** The Credit_Score column clearly separates the two Loan_Status groups. All other pairwise combinations show no visible clustering, confirming credit score is the sole driver.

---

#### 7. Violin Plot

```python
plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
sns.violinplot(x='Loan_Status', y='Credit_Score', data=df, palette='Set2', inner='quartile')
plt.title('Credit Score by Loan Status')

plt.subplot(1, 2, 2)
sns.violinplot(x='Loan_Status', y='Income', data=df, palette='Set2', inner='quartile')
plt.title('Income by Loan Status')

plt.tight_layout()
plt.show()
```

**Insight:** The Credit Score violin plots show two completely non-overlapping distributions. The Income violin plots are nearly identical, further confirming income does not affect approval.

---

#### 8. Joint Plot — Bivariate with Marginals

```python
joint = sns.jointplot(x='Income', y='Loan_Amount', data=df,
                       kind='reg', height=6,
                       marginal_kws=dict(bins=20, fill=True))
joint.fig.suptitle('Joint Distribution: Income vs Loan Amount', y=1.02)
plt.show()
```

**Insight:** `kind='reg'` adds a regression line with confidence band. The marginal histograms on each axis show the individual distributions. The near-flat regression line confirms no correlation between Income and Loan Amount.

---

#### 9. Subplots — 2×2 Dashboard

```python
fig, axes = plt.subplots(2, 2, figsize=(12, 10))

# Panel 1: Credit Score KDE by Loan Status
sns.kdeplot(data=df, x='Credit_Score', hue='Loan_Status', ax=axes[0, 0], fill=True, palette='Set1')

# Panel 2: Income Histogram with mean line
sns.histplot(data=df, x='Income', bins=20, ax=axes[0, 1], color='teal', edgecolor='black')
axes[0, 1].axvline(df['Income'].mean(), color='red', linestyle='--')

# Panel 3: Loan Amount Boxplot by Age Group
sns.boxplot(data=df, x='Age_Group', y='Loan_Amount', ax=axes[1, 0], palette='coolwarm')

# Panel 4: Credit Score vs Income Scatter coloured by Loan Amount
scatter = axes[1, 1].scatter(df['Credit_Score'], df['Income'],
                              c=df['Loan_Amount'], cmap='plasma', alpha=0.6)
plt.colorbar(scatter, ax=axes[1, 1], label='Loan Amount')

plt.tight_layout()
plt.savefig('dashboard_plot.png', dpi=100, bbox_inches='tight')
plt.show()
```

**Insight:** `plt.savefig()` exports the figure to disk. The `bbox_inches='tight'` argument prevents clipping of axis labels.

---

#### 10. Statistical Summary

```python
print(df[['Age', 'Income', 'Loan_Amount', 'Credit_Score', 'DTI']].describe().round(2))
print(df[['Age', 'Income', 'Loan_Amount', 'Credit_Score']].skew().round(3))
print(df[['Age', 'Income', 'Loan_Amount', 'Credit_Score']].kurtosis().round(3))
print(df['Loan_Status'].value_counts(normalize=True).round(4) * 100)
```

**Key Output:**

| Statistic | Age | Income | Loan_Amount | Credit_Score |
|---|---|---|---|---|
| Mean | 38.32 | 55,314 | 27,423 | 588.75 |
| Std | 11.76 | 24,181 | 13,448 | 167.11 |
| Skewness | 0.137 | 0.373 | 0.110 | 0.175 |
| Kurtosis | -1.224 | -1.103 | -1.303 | -1.133 |

**Insight:** All kurtosis values are negative (platykurtic), consistent with uniform random generation — flatter distributions with lighter tails than a normal distribution.

---

#### 11. Countplot with Hue

```python
plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
sns.countplot(data=df, x='Age_Group', hue='Loan_Status', palette='Set1')
plt.title('Loan Status by Age Group')
plt.xticks(rotation=15)

plt.subplot(1, 2, 2)
sns.countplot(data=df, x='Credit_Category', hue='Loan_Status', palette='Set2')
plt.title('Loan Status by Credit Category')
plt.xticks(rotation=20)

plt.tight_layout()
plt.show()
```

**Insight:** Young applicants (20–30) have the highest approval count. The Credit Category countplot visually confirms the hard threshold — no approvals below 600, no rejections above it.

---

#### 12. Stacked Bar Chart

```python
status_by_age = df.groupby(['Age_Group', 'Loan_Status']).size().unstack(fill_value=0)

colors = ['#ff6b6b', '#4ecdc4']
ax = status_by_age.plot(kind='bar', stacked=True, figsize=(8, 5),
                         color=colors, edgecolor='black')

for container in ax.containers:
    ax.bar_label(container, label_type='center', fontsize=9)

plt.title('Loan Status Distribution by Age Group')
plt.xticks(rotation=15)
plt.tight_layout()
plt.show()
```

**Key Output:**

| Age Group | Approved | Rejected |
|---|---|---|
| Young (20–30) | 19 | 14 |
| Middle (31–40) | 11 | 12 |
| Senior (41–50) | 8 | 17 |
| Mature (51–60) | 9 | 10 |

**Insight:** Approval rate declines with age in this dataset. `ax.bar_label()` adds count labels directly inside stacked segments.

---

#### 13. KDE Plot

```python
plt.figure(figsize=(10, 5))

# Credit Score KDE by Loan Status with threshold line
plt.subplot(1, 2, 1)
for status in df['Loan_Status'].unique():
    subset = df[df['Loan_Status'] == status]
    sns.kdeplot(data=subset, x='Credit_Score', label=status, fill=True, alpha=0.5)
plt.axvline(x=600, color='black', linestyle='--', label='Threshold (600)')
plt.title('Credit Score KDE by Loan Status')
plt.legend()

# Income KDE by Age Group
plt.subplot(1, 2, 2)
for age_group in ['Young (20-30)', 'Middle (31-40)', 'Senior (41-50)', 'Mature (51-60)']:
    subset = df[df['Age_Group'] == age_group]
    sns.kdeplot(data=subset, x='Income', label=age_group, fill=True, alpha=0.3)
plt.title('Income Distribution by Age Group')
plt.legend(fontsize=8)

plt.tight_layout()
plt.show()
```

**Insight:** The dashed threshold line at 600 clearly bisects the two KDE curves, making the approval boundary immediately visible. Income KDEs largely overlap, confirming no income bias.

---

#### 14. Swarm Plot

```python
plt.figure(figsize=(8, 5))
sns.swarmplot(data=df, x='Loan_Status', y='Credit_Score',
              hue='Age_Group', palette='tab10', size=6)
plt.axhline(y=600, color='red', linestyle='--', alpha=0.7, label='Approval Threshold')
plt.title('Swarm Plot: Credit Score by Loan Status\n(Color = Age Group)')
plt.legend(bbox_to_anchor=(1.05, 1), loc='upper left')
plt.tight_layout()
plt.show()
```

**Insight:** Swarm plots display every individual data point without overlap. `bbox_to_anchor=(1.05, 1)` places the legend outside the plot area to avoid obscuring data.

---

#### 15. Summary Statistics Table

```python
summary_by_status = df.groupby('Loan_Status').agg({
    'Customer_ID':   'count',
    'Credit_Score':  'mean',
    'Income':        'mean',
    'Loan_Amount':   'mean',
    'DTI':           'mean'
}).round(2)
summary_by_status.columns = ['Count', 'Avg_Credit', 'Avg_Income', 'Avg_Loan', 'Avg_DTI']
```

**Final Summary:**

| Loan_Status | Count | Avg Credit | Avg Income | Avg Loan | Avg DTI |
|---|---|---|---|---|---|
| Approved | 47 | 741.77 | 54,959 | 26,943 | 61.69% |
| Rejected | 53 | 453.06 | 55,629 | 27,849 | 61.31% |

---

## 6. Key Learnings

### 6.1 Chart Type Selection Guide

| Chart Type | Function | Purpose |
|---|---|---|
| Area Plot | `plt.fill_between()` | Show magnitude of values over a sequence; overlap two series for comparison |
| Pie Chart | `plt.pie()` | Part-to-whole proportions for a small number of categories |
| Donut Chart | `plt.pie()` + `plt.Circle()` | Same as pie but with centre removed for aesthetic clarity |
| Boxplot | `sns.boxplot()` / `plt.boxplot()` | Show median, IQR, and outliers for a numeric variable |
| Heatmap | `sns.heatmap()` | Visualise correlation matrix or any 2D numeric grid |
| Bubble Plot | `plt.scatter(s=)` / `sns.scatterplot(size=)` | Scatter plot with a third numeric dimension encoded as marker size |
| Violin Plot | `sns.violinplot()` | Full distribution shape + quartile summary per category |
| Joint Plot | `sns.jointplot()` | Bivariate relationship with marginal distributions |
| Pair Plot | `sns.pairplot()` | All pairwise numeric relationships coloured by a category |
| KDE Plot | `sns.kdeplot()` | Smooth density estimate; better than histogram for comparing groups |
| Swarm Plot | `sns.swarmplot()` | All individual data points without overlap |
| Countplot | `sns.countplot()` | Frequency count per category with optional hue grouping |
| Stacked Bar | `df.plot(kind='bar', stacked=True)` | Compare totals and composition across categories |

---

### 6.2 Key Pandas Techniques

| Technique | Function | Description |
|---|---|---|
| GroupBy aggregation | `df.groupby().agg({})` | Apply multiple functions to multiple columns at once |
| Categorical binning | `pd.cut()` | Divide a numeric column into labelled bins |
| Conditional column | `np.where(condition, a, b)` | Create a binary column based on a condition |
| Pivot table | `pd.pivot_table()` | Summarise data across two categorical dimensions |
| Cross-tabulation | `pd.crosstab()` | Frequency table for two categorical variables |
| Normalised crosstab | `pd.crosstab(normalize='index')` | Row-wise percentage breakdown |
| Dense ranking | `df.col.rank(method='dense')` | Rank without gaps on ties |
| Top-N rows | `df.nsmallest(n, col)` | Retrieve N rows with the smallest values in a column |
| Descriptive stats | `df.describe()` | Count, mean, std, min, quartiles, max |
| Skewness | `df.skew()` | Measure of distribution asymmetry |
| Kurtosis | `df.kurtosis()` | Measure of tail heaviness relative to normal distribution |

---

### 6.3 Key Matplotlib / Seaborn Parameters

| Parameter | Used In | Effect |
|---|---|---|
| `alpha=` | `fill_between`, `scatter` | Transparency (0 = invisible, 1 = opaque) |
| `autopct='%1.2f%%'` | `plt.pie()` | Format percentage labels on slices |
| `fc=` | `plt.Circle()` | Face colour of the donut centre circle |
| `s=` | `plt.scatter()` | Marker size (scalar or array) |
| `size=` / `sizes=` | `sns.scatterplot()` | Bubble size column and (min, max) range |
| `hue=` | Seaborn plots | Colour-encode a categorical or numeric column |
| `inner='quartile'` | `sns.violinplot()` | Draw quartile lines inside the violin |
| `kind='reg'` | `sns.jointplot()` | Add regression line to joint plot |
| `corner=True` | `sns.pairplot()` | Show only lower triangle of pair grid |
| `normalize='index'` | `pd.crosstab()` | Row-wise percentage normalisation |
| `stacked=True` | `df.plot(kind='bar')` | Stack bars instead of grouping side by side |
| `bbox_to_anchor=` | `plt.legend()` | Position legend outside the plot axes |
| `plt.savefig()` | Any figure | Export figure to file; use `bbox_inches='tight'` |

---

### 6.4 Best Practices

1. Always use `np.random.seed()` before generating synthetic datasets for reproducibility.
2. Use `pd.cut()` rather than manual `if/else` chains when binning numeric data into ordered categories.
3. Add `plt.colorbar()` whenever colour encodes a continuous numeric variable in a scatter or bubble plot.
4. Use `plt.tight_layout()` in all multi-panel figures to prevent axis label overlap.
5. Use `normalize='index'` in `pd.crosstab()` to convert raw counts to row percentages for fair comparison across groups of different sizes.
6. Prefer `sns.kdeplot()` over histograms when comparing distributions of two or more groups on the same axes.
7. Use `ax.bar_label(container, label_type='center')` to annotate stacked bar segments directly instead of manually computing label positions.
8. Save important dashboard figures with `plt.savefig('file.png', dpi=100, bbox_inches='tight')` before `plt.show()`, as `show()` clears the figure.

---

## 7. Observations

- Area and pie/donut charts on Dataset 1 confirm category D has the highest values (90), followed by B (70), E (60), C (30), and A (0).
- The bubble plot on Dataset 1 shows no clear relationship between Sales and Profit, consistent with independent random generation.
- All four numeric columns in Dataset 2 (Age, Income, Loan_Amount, Credit_Score) have correlations close to zero, confirming independence.
- Credit score alone determines loan approval — the threshold of 600 creates a perfect binary split with no ambiguous cases.
- Approved and rejected applicants have nearly identical average incomes ($54,959 vs $55,629) and DTI ratios (61.69% vs 61.31%).
- Negative kurtosis across all columns confirms platykurtic (flatter than normal) distributions, consistent with uniform random generation.
- Young applicants (20–30) have the highest approval count (19 out of 33), while Senior applicants (41–50) have the lowest approval rate (8 out of 25).
- The swarm plot makes the 600 credit score threshold immediately visible as a hard horizontal boundary.

---

## 8. Conclusion

This experiment successfully demonstrated a broad range of statistical and specialized visualization techniques across two datasets. Starting with compact 5-row categorical data for foundational chart types (area, pie, donut, boxplot, heatmap, bubble), the experiment progressed to a realistic 100-row loan applicant dataset for advanced analysis.

The self-learning section extended beyond the syllabus to cover GroupBy aggregations, feature engineering with `pd.cut()` and `np.where()`, pivot tables, cross-tabulation, dense ranking, and 15 distinct visualization techniques. A key insight throughout is that choosing the right chart type depends on the question being asked: KDE and violin plots for distribution comparison, joint plots for bivariate relationships, swarm plots for individual point visibility, and stacked bar charts for compositional comparison across groups.

---

## 9. References

- Matplotlib Documentation: https://matplotlib.org/stable/contents.html
- Seaborn Documentation: https://seaborn.pydata.org/
- Pandas Documentation: https://pandas.pydata.org/docs/
- NumPy Documentation: https://numpy.org/doc/
- Pandas GroupBy Guide: https://pandas.pydata.org/pandas-docs/stable/user_guide/groupby.html
- Seaborn Tutorial — Statistical Data Visualization: https://seaborn.pydata.org/tutorial.html
