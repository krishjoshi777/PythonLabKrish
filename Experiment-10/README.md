# Experiment 10: Creating and Uploading Dataset using Pandas
## Name : Krish Joshi
## Batch : EnTC A3
## PRN : 25070123064
________________________________________
## Aim
To create a dataset in Python and perform basic data inspection operations such as size, shape, info, and describe using Pandas.
________________________________________
## Objectives
•	To create a dataset using a dictionary
•	To convert it into a DataFrame
•	To upload/read a dataset from a CSV file
•	To perform basic data analysis using:
o	shape
o	size
o	info()
o	describe()
o	head() and tail()
________________________________________
## *Software Requirement*
•	Python 3.x
•	Pandas library
•	Jupyter Notebook / Google Colab / Python IDE
________________________________________ Theory
A dataset is a collection of related data. In Pandas, datasets are stored in the form of a DataFrame.
Datasets can be:
1.	Created manually
2.	Uploaded from external files such as:
o	CSV
o	Excel
o	JSON
o	SQL
o	
Basic inspection functions help to:
•	Understand the structure of the dataset
•	Identify missing values
•	Know data types
•	Get statistical summary
________________________________________
## *Basic Inspection Functions*
Function	Purpose
df.shape	Number of rows and columns
df.size	Total number of elements
df.info()	Structure of dataset
df.describe()	Statistical summary
df.head()	First 5 rows
df.tail()	Last 5 rows
df.columns	Display column names
________________________________________
# Program
Part A: Creating Dataset
import pandas as pd

data = {
    "Roll_No": [101, 102, 103, 104, 105],
    "Name": ["Amit", "Neha", "Rohit", "Sneha", "Kiran"],
    "Marks": [85, 90, 78, 88, 76],
    "Department": ["IT", "CS", "IT", "ENTC", "CS"]
}

df = pd.DataFrame(data)

print(df)
________________________________________
# Part B: Basic Dataset Inspection
print("Shape:", df.shape)

print("Size:", df.size)

print("\nColumn Names:\n", df.columns)

print("\nFirst 5 rows:\n", df.head())

print("\nLast 5 rows:\n", df.tail())

print("\nDataset Info:\n")
df.info()

print("\nStatistical Summary:\n", df.describe())
________________________________________Part C: Saving Dataset
df.to_csv("students.csv", index=False)
________________________________________Part D: Uploading / Reading Dataset
df2 = pd.read_csv("students.csv")

print("\nUploaded Dataset:\n", df2)
________________________________________
# Output
•	Dataset created successfully
•	Shape and size displayed
•	Column names shown
•	Dataset structure obtained using info()
•	Statistical summary generated
•	CSV file created and uploaded successfully
________________________________________
# Conclusion
Thus, the dataset was created and uploaded successfully, and basic inspection operations such as shape, size, info, and describe were performed using Pandas.


