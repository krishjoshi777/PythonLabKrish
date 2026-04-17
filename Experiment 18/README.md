# 📊 Real-World and Interactive Visualizations — Experiment 18

---

## 👤 Student Details

| Field | Details |
|---|---|
| **Name** | Krish Joshi |
| **PRN** | 25070123064 |
| **Class** | EnTC A3 |
| **Batch** | 2025–2029 |
| **Experiment No.** | 18 |
| **Date** | 10 April 2026 |

---

## 📌 Overview

This experiment explores a comprehensive range of real-world and interactive data visualization techniques using Python's Plotly ecosystem and supporting libraries. It moves beyond static charts to build fully interactive, web-ready visualizations that allow users to hover, rotate, filter, and animate data in real time.

The experiment is split into two parts: six core chart types covering hierarchical, relational, 3D, and multi-attribute visualizations; and fourteen self-learning advanced charts spanning geographic maps, animated time series, KPI dashboards, network graphs, and high-dimensional analysis tools.

---

## 🎯 Objectives

- Create hierarchical charts such as treemaps, dendrograms, and sunburst charts to represent nested data structures
- Build set and flow diagrams including Venn, Sankey, funnel, and waterfall charts for relational and sequential analysis
- Use 3D scatter and surface plots to explore multi-dimensional relationships interactively
- Construct radar and polar charts for directional and multi-attribute comparisons
- Build KPI dashboards using gauge, bullet, and Gantt charts
- Visualize geographic data with choropleth maps
- Animate scatter plots to illustrate temporal evolution
- Represent social and network relationships using graph theory with NetworkX
- Apply density contour plots for 2D distribution estimation
- Use parallel coordinates plots for high-dimensional multivariate analysis

---

## 🛠️ Tech Stack

| Library | Purpose |
|---|---|
| `plotly.express` | High-level, one-liner interactive charts |
| `plotly.graph_objects` | Low-level, fully customizable chart components |
| `plotly.subplots` | Multi-panel subplot layouts |
| `matplotlib` | Static base plotting and figure management |
| `matplotlib_venn` | Venn diagram rendering for set relationships |
| `scipy` | Hierarchical clustering via Ward's linkage |
| `networkx` | Graph creation, layout, and network analysis |
| `pandas` | Data structuring and aggregation |
| `numpy` | Numerical operations and grid generation |

---

## 📂 Project Structure

The repository contains the main Jupyter Notebook for all experiment sections, supporting dataset files, and this README documentation. All chart outputs are rendered interactively within the notebook and can be exported as standalone HTML files.

---

## 🔬 Methodology

### 1️⃣ Treemap — Company Budget Distribution
A treemap is used to represent company department budgets as nested rectangles, where the area of each rectangle is directly proportional to the budget value. The `path` parameter in Plotly Express defines the hierarchy levels. IT holds the largest budget while HR holds the smallest, making the distribution immediately visible at a glance.

---

### 2️⃣ Dendrogram — Hierarchical Clustering
A dendrogram is built using Ward's linkage from SciPy, which merges clusters by minimizing total within-cluster variance at each step. The y-axis represents the distance at which two clusters merge — taller branches indicate more dissimilar clusters. Five 2D data points are clustered and visualized to reveal their natural groupings.

---

### 3️⃣ Venn Diagram — Set Relationships
Two sets are defined and visualized using the `matplotlib_venn` library, which automatically computes and labels three regions: elements exclusive to Set A, elements in the intersection, and elements exclusive to Set B. The intersection represents shared elements between the two groups, making set logic immediately interpretable.

---

### 4️⃣ Sankey Diagram — Student Flow
A Sankey diagram tracks the journey of 100 students from admission through first year, second year, and final placement. The width of each connecting link is proportional to the number of students at that stage. The diagram reveals a 40% attrition rate overall — 20 students drop off at each transition — making it a powerful tool for tracking flow and loss across sequential stages.

---

### 5️⃣ 3D Scatter Plot — Student Performance
Three academic variables — study hours, marks, and attendance — are plotted simultaneously in a 3D interactive scatter plot. Plotly's built-in rotation capability allows the data cloud to be explored from any angle, revealing that higher study hours consistently correlate with higher marks and better attendance.

---

### 6️⃣ Radar Chart — Skill Assessment
A radar (spider) chart is constructed using Plotly's Scatterpolar trace to visualize a student's proficiency across five skills: Python, ML, DBMS, DSA, and Communication. The `fill='toself'` property shades the enclosed polygon, where the total area represents overall skill breadth. DBMS scores highest while ML and Communication are the areas for improvement.

---

## 🚀 Self-Learning — Advanced Interactive Visualizations

### 1. Sunburst Chart — Organizational Hierarchy
A sunburst chart visualizes a company's organizational structure with concentric rings — the inner ring showing departments and outer rings showing teams within each department. Slice sizes are proportional to headcount. Clicking any segment zooms into that branch for detailed exploration, making it ideal for hierarchical drill-down analysis.

### 2. Parallel Coordinates Plot — Multivariate Student Analysis
Fifty students' scores across Math, Physics, Chemistry, English, and Attendance are rendered as parallel vertical axes, with each student represented as a connected line. Lines following similar paths indicate similar students. High-performing students (color-coded in yellow) score consistently across all subjects. Axes can be dragged interactively to reorder and filter the dataset.

### 3. Animated Scatter Plot — GDP vs Life Expectancy
Eight countries are animated across 14 years (2010–2023) using GDP per capita on the x-axis and life expectancy on the y-axis. Bubble size encodes population. A logarithmic x-axis compresses the wide GDP range. Pressing Play traces each country's upward trajectory over time, revealing the relationship between economic growth and health outcomes.

### 4. Gauge Chart — System Performance Dashboard
Four KPIs — Server Uptime (98.5%), CPU Usage (65%), Memory Usage (78%), and Network Speed (125 Mbps) — are displayed as a 2×2 grid of gauge indicators. Color zones (green/yellow/red) give instant status feedback, and a red threshold line on the Uptime gauge marks the 99% SLA target. The `make_subplots` function with indicator type is required for this layout.

### 5. Funnel Chart — Sales Pipeline
Six stages of the sales pipeline from Website Visits (10,000) down to Purchase (800) are rendered as a funnel, with each bar showing both raw count and percentage of the top-of-funnel. Only 8% of visitors complete a purchase — a typical e-commerce pattern — and the largest single drop-off occurs between Product Views and Add to Cart at 55.6% conversion.

### 6. Waterfall Chart — Monthly Budget Analysis
A waterfall chart traces the cumulative financial impact of income and expenses starting from a $50,000 balance. Income adds $30,000, while Marketing, Operations, and R&D spend $35,000 combined, resulting in a net ending balance of $45,000. Green bars show inflows, red bars show outflows, and blue bars mark absolute totals.

### 7. Network Graph — Social Network Analysis
Eight people and their connections are modeled as a graph using NetworkX and rendered as an interactive Plotly scatter plot. Node size is proportional to degree centrality — the number of connections — so more influential nodes appear visually larger. Grace, Frank, and Charlie emerge as the top three connectors with four edges each. The Spring Layout algorithm positions highly connected nodes closer together.

### 8. Choropleth Map — World Population
A world map colors each country by population size using the Plasma color scale. The `natural earth` projection gives a familiar globe-like appearance, and hovering over any country reveals its GDP data alongside population. The `locationmode='country names'` parameter maps string country names directly to geographic boundaries.

### 9. Density Contour Plot — Height vs Weight Distribution
Five hundred synthetic data points across three body types (Average, Athletic, Slim) are visualized as a density contour plot with marginal histograms on both axes. Contour rings indicate concentration — tighter rings mean higher point density. The `selector=dict(type='contour')` filter in `update_traces` is critical to apply fill coloring only to the contour layer and not to the marginal histograms.

### 10. Polar Scatter Plot — Wind Speed and Direction
Wind speed readings at various compass directions are plotted in polar coordinates where the radius encodes speed and the angular position encodes direction. A dashed red warning circle at radius 25 marks the critical threshold. The clockwise angular direction matches standard compass convention with North at the top.

### 11. Gantt Chart — Project Timeline
Seven project tasks from Requirement Analysis through Deployment are displayed as a horizontal bar chart with a date x-axis. Overlapping bars reveal parallel tasks — Frontend and Backend development run concurrently — while color differentiates team assignments. Hovering reveals exact start and finish dates for each task.

### 12. 3D Surface Plot — Mathematical Function
The function z = sin(√(x² + y²)) is plotted over a 50×50 coordinate grid generated using NumPy's meshgrid, producing a circular ripple wave pattern radiating from the origin. Contour projections are enabled onto the base plane, creating a topographic shadow effect below the surface that aids spatial interpretation.

### 13. Multiple Radar Charts — Employee Skills Comparison
Three employees are compared across six skills on a single radar chart with overlapping semi-transparent polygons. Each polygon must be manually closed by appending the first element to complete the shape. Employee B leads in SQL, Communication, and Teamwork with the highest average score of 4.08/5.0, while Employee C leads in Python and Leadership.

### 14. Bullet Chart — KPI Performance vs Target
Four KPIs are stacked vertically using a combination of a wide background range bar for context, a narrow actual-value bar, and a target marker rendered as a scatter point. Only New Users (1,250 actual vs 1,000 target) exceeds its goal. Revenue, Customer Satisfaction, and Task Completion all fall short of their targets.

---

## 📊 Key Insights

- The Sankey diagram reveals a 40% attrition from admission to placement across three academic stages
- The sales funnel shows that only 8% of website visitors complete a purchase, with the sharpest drop between Product Views and Add to Cart
- The waterfall chart confirms a net $5,000 loss despite $30,000 income, as total expenses amount to $35,000
- Grace, Frank, and Charlie are the most connected nodes in the social network with 4 edges each
- Only New Users exceeds its KPI target in the bullet chart dashboard; all other metrics are below target
- The 3D surface of z = sin(√(x² + y²)) demonstrates how mathematical functions can be interactively explored in three dimensions
- Employee B holds the highest overall skill average of 4.08/5.0 across six competency areas

---

## ▶️ How to Run

1. **Clone the repository** — Download or clone this repo to your local machine.
2. **Install dependencies** — Install all required libraries: `plotly`, `matplotlib`, `matplotlib-venn`, `scipy`, `networkx`, `pandas`, and `numpy` using pip.
3. **Launch the notebook** — Open the experiment notebook in Jupyter Notebook, JupyterLab, or Google Colab for a zero-setup experience.
4. **Export charts** — Use `fig.write_html('filename.html')` to save any interactive Plotly chart as a standalone HTML file that works without a Python environment.

---

## 🔑 Key Learnings

### Plotly Express vs Graph Objects

Plotly Express (`px`) provides high-level, one-liner functions best suited for standard chart types such as treemaps, 3D scatter, choropleth maps, sunburst, animated scatter, parallel coordinates, Gantt charts, and density contours. Plotly Graph Objects (`go`) provides full low-level control and is required for custom layouts, subplots, and specialized chart types like Sankey diagrams, gauge indicators, funnel charts, waterfall charts, polar scatter, 3D surfaces, and bullet charts.

### Important Technical Notes
- Radar and polar polygons must be closed manually by appending the first data element to both the radius and theta arrays
- Animated scatter plots should always have fixed axis ranges to prevent misleading rescaling between frames
- Density contour `update_traces` calls require a `selector=dict(type='contour')` filter to avoid accidentally styling marginal histograms
- Network graphs built with NetworkX must be rendered manually as Plotly scatter traces since NetworkX does not natively produce Plotly figures
- The `make_subplots` function requires `specs=[{'type': 'indicator'}]` when placing gauge or indicator charts in a grid layout

---

## 📄 Conclusion

This experiment successfully demonstrated a broad range of real-world and interactive visualization techniques. The core six chart types established foundational knowledge in hierarchical, relational, 3D, and multi-attribute visualization. The fourteen self-learning charts extended this to geographic analysis, temporal animation, KPI dashboards, process funnels, network theory, and multivariate pattern detection.

The overarching principle is that interactive visualizations — unlike static plots — invite the audience to explore data directly through hovering, rotating, filtering, and animating. This makes them significantly more effective for dashboards, business intelligence, and data storytelling where user engagement and discovery are as important as the insight itself.

---

## 🔗 References

- Plotly Python Documentation: https://plotly.com/python/
- Plotly Express Reference: https://plotly.com/python-api-reference/plotly.express.html
- NetworkX Documentation: https://networkx.org/documentation/stable/
- SciPy Hierarchical Clustering: https://docs.scipy.org/doc/scipy/reference/cluster.hierarchy.html
- Matplotlib-Venn: https://pypi.org/project/matplotlib-venn/
- Pandas Documentation: https://pandas.pydata.org/docs/
- NumPy Documentation: https://numpy.org/doc/

---

<div align="center">
  <strong>Krish Joshi</strong> | EnTC A3 | PRN: 25070123064 | Batch 2025–2029
</div>
