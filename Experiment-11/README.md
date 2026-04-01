# Experiment-11
## Title: Categorical Data Analysis using Python
## Aim
To perform categorical data analysis using Python by identifying categories, calculating frequency distributions, performing cross-tabulation, and visualizing categorical variables.

# Theory
### 1. Categorical Data
Categorical data is a type of data that represents groups, labels, or categories instead of numerical values. These values describe qualities or characteristics and cannot be measured numerically.
Examples:
•	Gender (Male/Female)
•	Product Category (Electronics, Clothing, Grocery)
•	Payment Method (Cash, Card, UPI)
•	Customer Type (New, Returning)
Categorical data is widely used in business analytics, social sciences, marketing analysis, and survey data analysis.

### 2. Types of Categorical Data
Nominal Data
Nominal data represents categories without any natural order.
Examples:
•	Department (IT, CSE, Mechanical)
•	City (Pune, Mumbai, Delhi)
•	Blood Group (A, B, AB, O)
Here, categories are only labels, and no ranking exists.


## Ordinal Data
Ordinal data represents categories that have a meaningful order or ranking.
Examples:
•	Satisfaction Level (Poor, Average, Good, Excellent)
•	Education Level (Diploma, Graduate, Postgraduate)
Although there is an order, the difference between categories cannot be measured numerically.

### 3. Importance of Categorical Data Analysis
Categorical data analysis helps in:
•	Understanding distribution of categories
•	Identifying relationships between variables
•	Summarizing data for decision making
•	Detecting patterns and trends
For example:
•	Which product category is sold the most?
•	Which payment method is preferred by customers?
•	How customer type varies across cities?

### 4. Common Operations in Categorical Data Analysis
### 1. Frequency Count
Counts the number of occurrences of each category.
Example:
Electronics → 3
Clothing → 3
Grocery → 2
In Python this is done using:
value_counts()




### 2. Unique Category Identification
Used to find distinct categories present in a dataset.
Example:
UPI, Card, Cash
In Python this is done using:
unique()

### 3. Cross-Tabulation
Cross-tabulation is used to analyze the relationship between two categorical variables.
Example:
Product Category	UPI	Card	Cash
Electronics	2	0	1
Clothing	0	2	1
This helps identify patterns between variables.
In Python:
pd.crosstab()

### 4. Grouping of Data
Grouping helps summarize data based on categories.
Example:
Number of orders by product category.
In Python:
groupby()


### 5. Role of Python in Categorical Data Analysis
Python provides powerful libraries for analyzing categorical data:
Library	Purpose
Pandas	Data manipulation and analysis
Conclusion
Categorical data analysis helps in understanding patterns, relationships, and distributions within qualitative data. Python libraries such as Pandas, Matplotlib, and Seaborn provide efficient tools to analyze and visualize categorical datasets.


