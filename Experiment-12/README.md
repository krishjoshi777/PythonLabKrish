# Experiment-12
## Title: Data Preprocessing and Handling Missing Values in Python
## Aim
To study data preprocessing techniques and perform handling of missing values using various Python functions and operations.

## Theory
Data preprocessing is the process of cleaning and preparing raw data before performing data analysis or building machine learning models.
Real-world datasets often contain:
•	Missing values
•	Incorrect data formats
•	Duplicate records
•	Inconsistent values
Handling these issues improves data quality and accuracy of analysis.
One of the most common preprocessing tasks is handling missing values.
Missing values may appear as:
•	NaN
•	NULL
•	Blank cells
•	Symbols like ?, -, NA

## Data Preprocessing Functions / Operations
1. Display First Records
Shows the first few rows of the dataset.
Function
head()

2. Display Last Records
Function
tail()

3. Display Dataset Information
Shows number of rows, columns, data types, and missing values.
Function
info()

4. Check Data Types
Function
dtypes

5. Identify Missing Values
Function
isnull()
Returns True for missing values.

6. Count Missing Values
Function
isnull().sum()
Displays the total missing values in each column.

7. Detect Non-Missing Values
Function
notnull()
Returns True for valid values.

8. Replace Missing Symbols
Sometimes missing values appear as special characters like ?.
Function
replace()
Used to convert symbols into NaN values.

## Methods to Handle Missing Values
1. Remove Rows with Missing Values
Function
dropna()
Removes rows containing missing data.

2. Remove Columns with Missing Values
Function
dropna(axis=1)
Removes columns containing missing values.

3. Fill Missing Values
Function
fillna()
Used to replace missing values with another value.

4. Replace Missing Values with Mean
Function
mean()
fillna()
Used for numerical data.

5. Replace Missing Values with Median
Function
median()
fillna()
Useful when the dataset contains outliers.

6. Replace Missing Values with Mode
Function
mode()
fillna()
Used for categorical data.

7. Forward Fill Method
Function
fillna(method='ffill')
Replaces missing values with the previous value.

8. Backward Fill Method
Function
fillna(method='bfill')
Replaces missing values with the next value.

Other Preprocessing Operations
Remove Duplicate Records
Function
drop_duplicates()

Count Unique Values
Function
nunique()

Display Unique Values
Function
unique()

## Conclusion:
Data preprocessing and missing value handling operations were studied using various Python functions.


