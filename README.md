# Pandas-A-Z



Pandas Code Examples: A Practical Guide
This repository contains a collection of practical code examples demonstrating fundamental and intermediate functionalities of the Pandas library in Python. It's designed to be a quick reference and learning resource for anyone working with data manipulation and analysis using Pandas.

Table of Contents
Data Structures in Pandas

Series (1D)

DataFrame (2D)

Arithmetic Operations

Data Manipulation

Inserting Data

Slicing Data

Deleting Data

Accessing Rows and Columns (.loc, .iloc)

Working with CSV Files

Creating CSV Files

Reading CSV Files

Handling Missing Data

dropna()

fillna()

Getting Started

Contributing

License

Data Structures in Pandas
Pandas introduces two primary data structures: Series (1-dimensional) and DataFrame (2-dimensional).

Series (1D)
A Series is a one-dimensional labeled array capable of holding any data type (integers, strings, floats, Python objects, etc.).

Example 1: Basic Series Creation

import pandas as pd

x = [1, 2, 3, 4, 5]
print(x)
print()

var = pd.Series(x)
print(var)

Output:

[1, 2, 3, 4, 5]

0    1
1    2
2    3
3    4
4    5
dtype: int64

Example 2: Series with Custom Index and Data Type

You can specify a custom index and data type for your Series.

import pandas as pd

x = [1, 2, 3, 4]
var = pd.Series(x, index=["a", "b", "c", "d"], dtype="float")
print(var)

Output:

a    1.0
b    2.0
c    3.0
d    4.0
dtype: float64

Example 3: Series with Same Data and Custom Index

import pandas as pd

s = pd.Series("bilawal", index=[1, 2, 3, 4, 5, 6])
print(s)

Output:

1    bilawal
2    bilawal
3    bilawal
4    bilawal
5    bilawal
6    bilawal
dtype: object

Example 4: Handling Missing Data in Series (Arithmetic Operations)

When performing arithmetic operations on Series with misaligned indices, Pandas automatically introduces NaN (Not a Number) for missing values.

import pandas as pd

s1 = pd.Series(12, index=[1, 2, 3, 4, 5, 6, 7, 8, 9])
s2 = pd.Series(12, index=[2, 3, 5, 6, 7, 8])
print(s1 + s2)

Output:

1     NaN
2    24.0
3    24.0
4     NaN
5    24.0
6    24.0
7    24.0
8    24.0
9     NaN
dtype: float64

DataFrame (2D)
A DataFrame is a two-dimensional labeled data structure with columns of potentially different types. It's similar to a spreadsheet or SQL table.

Example 1: Creating DataFrame from a List with Custom Index

import pandas as pd

data_list = [1, 2, 3, 4, 5, 6]
names = ["Bilal", "Sahid", "Ali", "Ahmed", "Yasir", "Adnan"]
var = pd.DataFrame(data_list, index=names) # Note: Index is for rows here
print(type(var))
print(var)

Output:

<class 'pandas.core.frame.DataFrame'>
         0
Bilal    1
Sahid    2
Ali      3
Ahmed    4
Yasir    5
Adnan    6

Example 2: Creating DataFrame from a Dictionary

Dictionaries are a common way to create DataFrames, where keys become column names.

import pandas as pd

dic = {"countries": ["UK", "USA", "UAE", "KSA"],
       "FULL NAME": ["UNITEDKINGDOM", "UNITED STATE", "UNITED ARAB EMIR", "KINGDUM OF S.A"]}
var = pd.DataFrame(dic)
print(var)

Output:

  countries         FULL NAME
0        UK     UNITEDKINGDOM
1       USA      UNITED STATE
2       UAE  UNITED ARAB EMIR
3       KSA    KINGDUM OF S.A

Example 3: Accessing a Column in a DataFrame

import pandas as pd

dic = {"countries": ["UK", "USA", "UAE", "KSA"],
       "FULL NAME": ["UNITEDKINGDOM", "UNITED STATE", "UNITED ARAB EMIR", "KINGDUM OF S.A"]}
var = pd.DataFrame(dic)
print(var["FULL NAME"])

Output:

0       UNITEDKINGDOM
1        UNITED STATE
2    UNITED ARAB EMIR
3      KINGDUM OF S.A
Name: FULL NAME, dtype: object

Example 4: Creating DataFrame from Series

You can combine multiple Series into a DataFrame.

import pandas as pd

sr = {"r": pd.Series([1, 2, 3, 4, 5, 6, 7, 8, 9]),
      "s": pd.Series([10, 11, 12, 13, 14, 15, 17, 18, 19])}
var = pd.DataFrame(sr)
print(var)

Output:

   r   s
0  1  10
1  2  11
2  3  12
3  4  13
4  5  14
5  6  15
6  7  17
7  8  18
8  9  19

Arithmetic Operations
Pandas DataFrames support various arithmetic operations between columns or with scalar values.

Example 1: Basic DataFrame for Arithmetic

import pandas as pd

dic = {"a": [1, 2, 3, 4, 5, 6], "b": [7, 8, 9, 1, 2, 3]}
var = pd.DataFrame(dic)
print(var)

Output:

   a  b
0  1  7
1  2  8
2  3  9
3  4  1
4  5  2
5  6  3

Example 2: Adding two columns to create a new one

import pandas as pd

var = pd.DataFrame({"a": [1, 2, 3, 4, 5, 6], "b": [7, 8, 9, 1, 2, 3]})
var["c"] = var["a"] + var["b"]
print(var)

Output:

   a  b   c
0  1  7   8
1  2  8  10
2  3  9  12
3  4  1   5
4  5  2   7
5  6  3   9

Example 3: Subtracting two columns

import pandas as pd

var = pd.DataFrame({"a": [1, 2, 3, 4, 5, 6], "b": [7, 8, 9, 1, 2, 3]})
var["c"] = var["a"] - var["b"]
print(var)

Output:

   a  b  c
0  1  7 -6
1  2  8 -6
2  3  9 -6
3  4  1  3
4  5  2  3
5  6  3  3

Example 4: Modulo operation between columns

import pandas as pd

var = pd.DataFrame({"a": [1, 2, 3, 4, 5, 6], "b": [7, 8, 9, 1, 2, 3]})
var["c"] = var["a"] % var["b"]
print(var)

Output:

   a  b  c
0  1  7  1
1  2  8  2
2  3  9  3
3  4  1  0
4  5  2  1
5  6  3  0

Example 5: Floor division between columns

import pandas as pd

var = pd.DataFrame({"a": [1, 2, 3, 4, 5, 6], "b": [7, 8, 9, 1, 2, 3]})
var["c"] = var["a"] // var["b"]
print(var)

Output:

   a  b  c
0  1  7  0
1  2  8  0
2  3  9  0
3  4  1  4
4  5  2  2
5  6  3  2

Example 6: Exponentiation between columns

import pandas as pd

var = pd.DataFrame({"a": [1, 2, 3, 4, 5, 6], "b": [7, 8, 9, 1, 2, 3]})
var["c"] = var["a"] ** var["b"]
print(var)

Output:

   a  b      c
0  1  7      1
1  2  8    256
2  3  9  19683
3  4  1      4
4  5  2     25
5  6  3    216

Example 7: Boolean Comparison

import pandas as pd

var = pd.DataFrame({"a": [1, 2, 10, 4, 50, 6], "b": [7, 8, 9, 1, 2, 3]})
var["TRUE/FALSE"] = var["a"] < 10
print(var)

Output:

    a  b  TRUE/FALSE
0   1  7        True
1   2  8        True
2  10  9       False
3   4  1        True
4  50  2       False
5   6  3        True

Data Manipulation
Inserting Data
You can insert new columns into a DataFrame at a specific position   . 

import pandas as pd

var = pd.DataFrame({"A": [1, 2, 3, 4, 5], "B": [6, 7, 8, 9, 10]})
print("Original DataFrame:")
print(var)

# Insert column 'c' at position 2 (0-indexed), copying values from column 'A'
var.insert(2, "c", var["A"])
print("\nDataFrame after inserting 'c':")
print(var)

Output:

Original DataFrame:
   A   B
0  1   6
1  2   7
2  3   8
3  4   9
4  5  10

DataFrame after inserting 'c':
   A   B   c
0  1   6   1
1  2   7   2
2  3   8   3
3  4   9   4
4  5  10   5

Slicing Data
Slicing allows you to select a range of rows from a DataFrame.

Example 1: Slicing from the beginning

import pandas as pd

# Assuming 'customers-100.csv' is available in the same directory or path
var = pd.read_csv("customers-100.csv")
print(var[:6]) # Selects rows from index 0 up to (but not including) 6

Example 2: Slicing a specific range

import pandas as pd

# Assuming 'customers-100.csv' is available in the same directory or path
var = pd.read_csv("customers-100.csv")
print(var[5:11]) # Selects rows from index 5 up to (but not including) 11

Deleting Data
You can remove columns from a DataFrame using pop() or del.

Example 1: Using pop() to remove a column

pop() removes a column and returns it as a Series.

import pandas as pd

bilawal = pd.DataFrame({"A": [1, 2, 3, 4, 5], "B": [6, 7, 8, 9, 10], "C": [2, 4, 6, 8, 1]})
print("Original DataFrame:")
print(bilawal)

a = bilawal.pop("B")
print("\nRemoved Series 'B':")
print(a)
print("\nDataFrame after pop('B'):")
print(bilawal)

Output:

Original DataFrame:
   A   B  C
0  1   6  2
1  2   7  4
2  3   8  6
3  4   9  8
4  5  10  1

Removed Series 'B':
0     6
1     7
2     8
3     9
4    10
Name: B, dtype: int64

DataFrame after pop('B'):
   A  C
0  1  2
1  2  4
2  3  6
3  4  8
4  5  1

Example 2: Using del to remove a column

del removes a column in place.

import pandas as pd

var = pd.DataFrame({"A": [1, 2, 3, 4, 5], "B": [6, 7, 8, 9, 10], "C": [2, 4, 6, 8, 1]})
print("Original DataFrame:")
print(var)

del var["A"]
print("\nDataFrame after del var['A']:")
print(var)

Output:

Original DataFrame:
   A   B  C
0  1   6  2
1  2   7  4
2  3   8  6
3  4   9  8
4  5  10  1

DataFrame after del var['A']:
    B  C
0   6  2
1   7  4
2   8  6
3   9  8
4  10  1

Accessing Rows and Columns (.loc, .iloc)
Pandas provides .loc for label-based indexing and .iloc for integer-based indexing.

Example 1: Selecting specific rows and columns using .loc

import pandas as pd

# Assuming 'customers-100.csv' is available
var = pd.read_csv("customers-100.csv")
print(var.loc[[6, 7], ["City", "Country"]])

Output (example):

        City        Country
6  Lake Ana  Pitcairn Islands
7   Kimport          Bulgaria

Example 2: Selecting specific rows using .loc

import pandas as pd

# Assuming 'customers-100.csv' is available
var = pd.read_csv("customers-100.csv")
print(var.loc[[3, 7]])

Example 3: Selecting specific rows using .iloc

.iloc uses integer positions for both rows and columns.

import pandas as pd

# Assuming 'customers-100.csv' is available
var = pd.read_csv("customers-100.csv")
print(var.iloc[[2, 3], :]) # Selects rows at integer positions 2 and 3, all columns

Working with CSV Files
Pandas makes it easy to read from and write to CSV (Comma Separated Values) files.

Creating CSV Files
You can export a DataFrame to a CSV file using to_csv().

import pandas as pd

dic = {"a": [1, 2, 3, 4, 5], "b": [2, 4, 6, 7, 8], "c": [3, 6, 9, 3, 6]}
var = pd.DataFrame(dic)
print("DataFrame to be saved:")
print(var)

# Save to CSV
var.to_csv("pandas_course.csv")
print("\n'pandas_course.csv' created successfully.")

Output:

   a  b  c
0  1  2  3
1  2  4  6
2  3  6  9
3  4  7  3
4  5  8  6

'pandas_course.csv' created successfully.

Reading CSV Files
You can read data from a CSV file into a DataFrame using read_csv().

Example 1: Reading an entire CSV file

import pandas as pd

# Assuming 'covid.csv' is available in the same directory or path
# Note: For large files, printing the entire DataFrame with print(df.to_string())
# might exceed output limits in some environments (like Jupyter notebooks).
df = pd.read_csv("covid.csv")
print(df)

Example 2: Reading a specific number of rows

Use the nrows parameter to read only the first N rows.

import pandas as pd

# Assuming 'covid.csv' is available
df = pd.read_csv("covid.csv", nrows=1)
print(df)

Output (first row example):

  Direction  Year        Date   Weekday Country Commodity Transport_Mode  \
0   Exports  2015  01/01/2015  Thursday     All       All            All

  Measure      Value  Cumulative
0       $  104000000   104000000

Example 3: Reading specific columns

Use the usecols parameter to load only desired columns.

import pandas as pd

# Assuming 'covid.csv' is available
df = pd.read_csv("covid.csv", usecols=["Year"])
print(df)

Output (example):

        Year
0       2015
1       2015
2       2015
3       2015
4       2015
...      ...
111433  2021
111434  2021
111435  2021
111436  2021
111437  2021

[111438 rows x 1 columns]

Handling Missing Data
Missing data (often represented as NaN - Not a Number) is common in real-world datasets. Pandas provides robust tools to manage it.

dropna()
The dropna() method is used to remove rows or columns containing missing values.

Example 1: Dropping rows with any NaN values

By default, dropna() removes any row that contains at least one NaN value.

import pandas as pd

# Assuming 'customers-100.csv' is available
var = pd.read_csv("customers-100.csv")
print("Original DataFrame shape:", var.shape)
df_cleaned = var.dropna()
print("DataFrame after dropna() (default 'any'):")
print(df_cleaned.shape) # Print shape to show rows removed
print(df_cleaned.head()) # Show first few rows of cleaned data

Example 2: how="any" (explicitly)

This is the default behavior, removing a row if any NaN is present.

import pandas as pd

# Assuming 'customers-100.csv' is available
var = pd.read_csv("customers-100.csv")
df_any = var.dropna(how="any")
print("DataFrame after dropna(how='any'):")
print(df_any.shape)
print(df_any.head())

Notes on dropna() parameters:

how="all": Drops a row/column only if all its values are NaN.

subset=["column_name"]: Drops rows where NaN values are present only in the specified column(s).

inplace=True: Modifies the DataFrame directly instead of returning a new one.

thresh=N: Requires at least N non-NaN values for a row/column to be kept.

fillna()
The fillna() method is used to replace missing values with a specified value or method.

Example 1: Filling NaN with a single value

import pandas as pd

# Assuming 'customers-100.csv' is available
var = pd.read_csv("customers-100.csv")
# Introduce some NaNs for demonstration if the CSV is clean
var.loc[0, 'Phone 2'] = None
var.loc[2, 'Website'] = None

print("DataFrame with introduced NaNs:")
print(var.head())

df_filled = var.fillna("python")
print("\nDataFrame after fillna('python'):")
print(df_filled.head())

Example 2: Filling NaN with different values for different columns

import pandas as pd

# Assuming 'customers-100.csv' is available
var = pd.read_csv("customers-100.csv")
# Introduce some NaNs for demonstration
var.loc[0, 'Country'] = None
var.loc[1, 'Phone 1'] = None

print("DataFrame with introduced NaNs:")
print(var.head())

df_filled_col = var.fillna({"Country": "Sri Lanka", "Phone 1": "034343434"})
print("\nDataFrame after fillna with dictionary:")
print(df_filled_col.head())

Example 3: Filling NaN using forward fill (ffill)

ffill propagates the last valid observation forward to next valid observation.

import pandas as pd

# Assuming 'customers-100.csv' is available
var = pd.read_csv("customers-100.csv")
# Introduce some NaNs for demonstration
var.loc[1, 'City'] = None
var.loc[3, 'City'] = None

print("DataFrame with introduced NaNs:")
print(var.iloc[0:5, [5, 6]]) # Show relevant columns

df_ffill = var.fillna(method="ffill")
print("\nDataFrame after fillna(method='ffill'):")
print(df_ffill.iloc[0:5, [5, 6]])

Getting Started
To run these examples:

Clone this repository:

git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name

(Replace your-username/your-repo-name.git with the actual path to your repository.)

Install Pandas:
If you don't have Pandas installed, you can do so using pip:

pip install pandas

(You might also need openpyxl if you plan to work with Excel files: pip install openpyxl)

Obtain Data Files:
The examples use covid.csv and customers-100.csv. Please ensure these files are present in the same directory as your Python scripts, or update the file paths in the code accordingly. You can find sample customers-100.csv files online or create one for testing. For covid.csv, you'd need a similar dataset.

Run a specific example:
Each code snippet is self-contained. You can copy and paste them into a Python interpreter, a Jupyter Notebook, or save them as individual .py files and run them from your terminal:

python your_script_name.py

Contributing
Contributions are highly welcome! If you have more Pandas examples, improvements to existing ones, or find any issues, please feel free to:

Fork the repository.

Create a new branch (git checkout -b feature/your-new-feature).

Make your changes.

Commit your changes (git commit -m 'Add new example for X').

Push to the branch (git push origin feature/your-new-feature).

Open a Pull Request.

> 

---- BB 
Linkedin: @BILAWAL BASHIR
