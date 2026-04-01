# Title: Data Normalization and Turning Categorical Variables into Quantitative Variables in Python

## Aim
To study and perform data normalization and convert categorical variables into quantitative variables using various Python functions and operations.

## Theory
In data analysis and machine learning, raw data often contains different scales of numerical values and categorical variables. Before analysis, the data must be preprocessed so that it becomes suitable for computational models.
Two important preprocessing techniques are:
•	Data Normalization
•	Categorical Variable Encoding
These techniques help in improving data quality, consistency, and analysis accuracy.
________________________________________
1. Data Normalization
Definition
Data normalization is a technique used to scale numerical data into a common range so that all features contribute equally to the analysis.
For example:
Feature	Range
Price	500 – 50000
Rating	1 – 5
Units Sold	10 – 1000
Without normalization, features with larger ranges dominate smaller ones.
Normalization helps to:
•	Standardize the scale of data
•	Improve performance of machine learning models
•	Make comparisons between variables easier
________________________________________
## Types of Normalization
1. Min-Max Normalization
This method scales values between 0 and 1.
Functions / Operations
min()
max()
These functions determine the minimum and maximum values required for scaling.
________________________________________
2. Z-score Normalization (Standardization)
This method transforms data based on mean and standard deviation.
Functions / Operations
mean()
std()
It indicates how far a value is from the average value of the dataset.
________________________________________
3. Decimal Scaling
In this method, the decimal point of values is shifted so that all values fall within a smaller range.
Operation
Division by powers of 10.
________________________________________
Useful Functions for Normalization
Summary Statistics
describe()
Displays statistical measures such as:
•	mean
•	standard deviation
•	minimum
•	maximum
________________________________________
## Identify Data Types
dtypes
Used to identify numerical columns that require normalization.
________________________________________
## Select Columns
loc[]
iloc[]
Used to apply normalization to specific columns of the dataset.
________________________________________
2. Turning Categorical Variables into Quantitative Variables
Definition
Many datasets contain categorical variables, which represent qualitative data.
Examples:
Variable	Values
Gender	Male, Female
Payment Method	UPI, Debit Card
Product Category	Electronics, Clothing
Most data analysis algorithms require numerical input, so categorical data must be converted into quantitative form.
This process is called categorical encoding.
________________________________________
Methods to Convert Categorical Data
1. Label Encoding
Each category is assigned a unique numeric value.
Example:
Category	Encoded Value
Male	0
Female	1
Functions / Operations
LabelEncoder()
fit_transform()
________________________________________
2. One-Hot Encoding
This method creates separate binary columns for each category.
Example:
Category	Electronics	Clothing	Home
Electronics	1	0	0
Functions / Operations
get_dummies()
________________________________________
3. Dummy Encoding
Similar to One-Hot Encoding but one column is removed to avoid redundancy.
Functions / Operations
get_dummies(drop_first=True)
________________________________________

## Conclusion
Data normalization and categorical variable transformation techniques were successfully studied using various Python functions and operations.

