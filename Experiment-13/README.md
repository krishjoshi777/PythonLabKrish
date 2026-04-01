# Experiment-13
## Title: Data Binning and Data Formatting in Python
## Aim
To study and perform data binning and data formatting techniques using various Python functions and operations.

## Theory
Data preprocessing is an essential step in data analysis. It involves transforming raw data into a more structured and meaningful format.
Two important preprocessing techniques are:
1. Data Binning
Data binning is the process of grouping continuous numerical data into intervals (bins).
It helps to:
•	Reduce noise in data
•	Simplify data analysis
•	Convert continuous data into categorical form
Example:
Age	Bin
18	Young
30	Adult
60	Senior

2. Data Formatting
Data formatting refers to converting data into a proper format or structure so that it can be easily processed and analyzed.
Examples:
•	Converting string to numeric values
•	Converting date formats
•	Changing text case
•	Removing extra spaces
Proper formatting improves data consistency and accuracy.

## Functions / Operations for Data Binning
1. Create Bins
Function
pd.cut()
Used to divide numerical data into equal intervals (bins).

2. Create Quantile-Based Bins
Function
pd.qcut()
Divides data into bins with equal number of observations.

3. Display Bin Counts
Function
value_counts()
Shows the frequency of values in each bin.

4. Define Custom Bin Labels
Function
labels
Used with binning functions to assign names to bins.
Example labels:
•	Low
•	Medium
•	High

## Functions / Operations for Data Formatting
1. Check Data Types
Function
dtypes
Displays the data type of each column.

2. Convert Data Types
Function
astype()
Used to convert one data type into another.
Examples:
•	string → integer
•	float → integer

3. Convert String to Numeric
Function
pd.to_numeric()
Used when numbers are stored as text values.

4. Convert to Date Format
Function
pd.to_datetime()
Used to convert values into date format.

5. Change Text Case
Functions
str.lower()
str.upper()
str.title()
Used to standardize text formatting.

6. Remove Extra Spaces
Function
str.strip()
Removes leading and trailing spaces.

7. Replace Values
Function
replace()
Used to replace incorrect or inconsistent values.


## Conclusion
Data binning and data formatting techniques were studied using various Python functions and operations.


