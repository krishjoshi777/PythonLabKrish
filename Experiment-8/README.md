# STUDY OF NUMPY LIBRARY (Python)

**Name:** Krish Joshi

**Branch:** EnTC A3

**PRN:** 25070123064

---

## 📘 Title Page

**Project Name:** Study of NumPy Library in Python

**Purpose:** Understanding NumPy Arrays and Operations

**Language:** Python


---

## 🎯 Aim of the Study

The aim of this project is to study the NumPy (Numerical Python) library and understand how it is used for numerical computations.

This project focuses on:

* Creating NumPy arrays
* Performing mathematical operations
* Understanding array properties
* Indexing and slicing
* Performing statistical and matrix operations

---

## 📌 Introduction

NumPy (Numerical Python) is one of the most powerful and widely used Python libraries for numerical and scientific computing.

It provides support for:

* Large multi-dimensional arrays
* Mathematical functions
* Linear algebra operations
* Statistical operations

NumPy is faster than Python lists because it is implemented in C and optimized for performance.

---

## 📖 Study of NumPy (Instructions)

1. Import NumPy library
2. Create NumPy arrays
3. Study array attributes (shape, size, ndim, dtype)
4. Perform indexing and slicing
5. Apply mathematical operations
6. Perform statistical functions
7. Understand reshaping and transformation of arrays
8. Compare NumPy arrays with Python lists

---

## 🔑 Key Concepts Covered

* Importing NumPy
* Creating arrays
* Array dimensions
* Array indexing
* Array slicing
* Array reshaping
* Mathematical operations
* Statistical operations
* Broadcasting
* Matrix operations

---

# 📘 THEORY (NumPy Library)

---

## 1️⃣ Importing NumPy

NumPy is imported using the keyword `import`.

```python
import numpy as np
```

Here, `np` is an alias (short name) used for convenience.

---

## 2️⃣ Creating NumPy Arrays

Arrays are created using `np.array()` function.

```python
arr = np.array([1, 2, 3, 4])
```

NumPy arrays are different from Python lists because:

* They are faster
* They require less memory
* They support vectorized operations

---

## 3️⃣ Types of Arrays

### 1D Array

```python
np.array([1, 2, 3])
```

### 2D Array

```python
np.array([[1, 2], [3, 4]])
```

### 3D Array

```python
np.array([[[1, 2], [3, 4]]])
```

---

## 4️⃣ Array Attributes

NumPy arrays have important attributes:

* `arr.ndim` → Number of dimensions
* `arr.shape` → Shape of array (rows, columns)
* `arr.size` → Total number of elements
* `arr.dtype` → Data type of elements

Example:

```python
arr = np.array([[1,2,3],[4,5,6]])
print(arr.shape)
```

---

## 5️⃣ Special Array Creation Functions

### zeros()

Creates array filled with zeros.

```python
np.zeros((2,3))
```

### ones()

Creates array filled with ones.

```python
np.ones((2,3))
```

### arange()

Creates array with evenly spaced values.

```python
np.arange(1, 10)
```

### linspace()

Creates array with specified number of evenly spaced values.

```python
np.linspace(0, 10, 5)
```

---

## 6️⃣ Indexing and Slicing

Indexing is used to access specific elements.

```python
arr[0]
arr[1,2]
```

Slicing is used to access a range of elements.

```python
arr[0:2]
arr[:,1]
```

NumPy slicing works similar to Python lists but supports multi-dimensional slicing.

---

## 7️⃣ Mathematical Operations

NumPy supports element-wise operations.

```python
arr + 5
arr * 2
arr1 + arr2
```

Operations include:

* Addition
* Subtraction
* Multiplication
* Division
* Power

These operations are faster compared to normal loops.

---

## 8️⃣ Statistical Functions

NumPy provides built-in statistical functions:

* `np.sum()` → Sum of elements
* `np.mean()` → Average
* `np.median()` → Median
* `np.max()` → Maximum value
* `np.min()` → Minimum value
* `np.std()` → Standard deviation

Example:

```python
np.mean(arr)
```

---

## 9️⃣ Reshaping Arrays

Reshaping changes the structure of an array.

```python
arr.reshape(2,3)
```

Important rule: Total elements must remain the same.

---

## 🔟 Matrix Operations

NumPy supports matrix multiplication.

```python
np.dot(arr1, arr2)
```

or

```python
arr1 @ arr2
```

It also supports:

* Transpose (`arr.T`)
* Determinant
* Inverse (using linear algebra module)

---

## 📊 Broadcasting

Broadcasting allows NumPy to perform operations on arrays of different shapes.

Example:

```python
arr + 10
```

Here, `10` is automatically added to every element.

---

## ✅ Advantages of NumPy

* Faster than Python lists
* Efficient memory usage
* Supports multi-dimensional arrays
* Built-in mathematical functions
* Used in Data Science and Machine Learning

---

## 📂 Applications of NumPy

* Data Science
* Machine Learning
* Artificial Intelligence
* Scientific Computing
* Financial Analysis
* Signal Processing
* Image Processing

---

## 🎯 Conclusion

NumPy is a powerful library for numerical computation in Python.

Through this study, we learned:

* How to create NumPy arrays
* How to access and modify elements
* How to perform mathematical and statistical operations
* How to reshape arrays
* How NumPy improves performance compared to Python lists

Understanding NumPy is essential for advanced topics like Pandas, Machine Learning, and Artificial Intelligence.

---

## 📎 Extra Notes

* NumPy arrays are homogeneous (same data type)
* Indexing starts from 0
* `reshape()` must maintain total elements
* NumPy is the foundation for data analysis libraries

