## Importing Entire Text File

```python
file = open('moby_dick.txt', 'r')
print(file.read())
file.close()
```

- Open the file named "moby_dick.txt" in read mode.
- Read and print the contents of the file.
- Close the file.
- Check if the file is closed (returns False).
- Re-check if the file is closed (returns True).

## Reading Line-by-Line

```python
with open('moby_dick.txt') as file:
    print(file.readline())
    print(file.readline())
    print(file.readline())
```

- Open the file named "moby_dick.txt".
- Using the `with` statement ensures that the file is properly closed.
- Read and print the first line of the file.
- Read and print the second line of the file.
- Read and print the third line of the file.

## Using NumPy to Import Flat Files

```python
import numpy as np

file = 'digits.csv'
digits = np.loadtxt(file, delimiter=',')
print(type(digits))
plt.imshow(digits[21, 1:].reshape(28, 28), cmap='Greys', interpolation='nearest')
plt.show()
```

- Import the NumPy package.
- Specify the file name as "digits.csv".
- Use `np.loadtxt()` to load the file as an array, specifying the delimiter as a comma (',').
- Print the datatype of the loaded array.
- Plot a specific row of the array as an image using Matplotlib.

## Customizing Your NumPy Import

```python
import numpy as np

file = 'digits_header.txt'
data = np.loadtxt(file, delimiter='\t', skiprows=1, usecols=[0, 2])
print(data)
```

- Import the NumPy package.
- Specify the file name as "digits_header.txt".
- Use `np.loadtxt()` to load the file as an array, specifying the delimiter as a tab ('\t').
- Skip the first row of the file using the `skiprows` parameter.
- Select only the columns at indices 0 and 2 using the `usecols` parameter.
- Print the resulting array.

## Working with Mixed Datatypes

```python
file = 'titanic.csv'
d = np.recfromcsv(file, dtype=None)
print(d[:3])
```

- Specify the file name as "titanic.csv".
- Use `np.recfromcsv()` to load the CSV file with mixed datatypes.
- Set the `dtype` parameter to `None` to infer the datatypes automatically.
- Print the first three entries of the resulting structured array.

## Working with Pandas

```python
import pandas as pd

file = 'titanic.csv'
df = pd.read_csv('titanic.csv')
print(df.head())
```

- Import the pandas package.
- Specify the file name as "titanic.csv".
- Use `pd.read_csv()` to read the CSV file into a DataFrame.
- Print the head of the DataFrame.

## Using Pandas to Import Flat Files as DataFrames

```python
file = 'digits.csv'
data = pd.read_csv(file, nrows=5, header=None)
data_array = np.array(data)
print(type(data_array))
```

- Specify the file name as "digits.csv".
- Use `pd.read_csv()` to read the first 5 rows of the CSV file into a DataFrame.
- Convert the DataFrame to a NumPy array using `np.array()`.
- Print the datatype of the resulting array.

## Customizing Your Pandas Import

```python
import pandas as pd
import matplotlib.pyplot as plt

file = 'titanic_corrupt.txt'
data = pd.read_csv(file, sep='\t', comment='#', na_values='Nothing')
print(data.head())

pd.DataFrame.hist(data[['Age']])
plt.xlabel('Age (years)')
plt.ylabel('count')
plt.show()
```

- Import the pandas and matplotlib.pyplot packages.
- Specify the file name as "titanic_corrupt.txt".
- Use `pd.read_csv()` to read the file into a DataFrame.
- Customize the import by specifying the separator as '\t', excluding lines starting with '#', and replacing 'Nothing' with NaN.
- Print the head of the DataFrame.
- Plot a histogram of the 'Age' variable using `pd.DataFrame.hist()` and display the plot.

## Other File Types

```python
import pickle

with open('data.pkl', 'rb') as file:
    d = pickle.load(file)

print(d)
print(type(d))
```

- Import the pickle package.
- Open the file named "data.pkl" in read mode and binary format ('rb').
- Load the data from the file using `pickle.load()`.
- Print the loaded data.
- Print the datatype of the loaded data.

## Excel File

```python
import pandas as pd

file = 'battledeath.xlsx'
xls = pd.ExcelFile(file)
print(xls.sheet_names)

df1 = xls.parse('2004')
print(df1.head())

df2 = xls.parse(0)
print(df2.head())
```

- Import the pandas package.
- Specify the file name as "battledeath.xlsx".
- Load the Excel file using `pd.ExcelFile()`.
- Print the names of the sheets in the Excel file.
- Parse the sheet named '2004' into a DataFrame using `xls.parse()`.
- Print the head of the DataFrame.
- Parse the first sheet (index 0) into a DataFrame using `xls.parse()`.
- Print the head of the DataFrame.

## Customizing Your Spreadsheet Import

```python
df1 = xls.parse(0, skiprows=[0], names=['Country', 'AAM due to War (2002)'])
print(df1.head())

df2 = xls.parse(1, usecols=[0], skiprows=[0], names=['Country'])
print(df2.head())
```

- Specify the sheet index (0) and customize the import by skipping the first row, renaming columns, and selecting specific columns.
- Print the head of the DataFrame.
- Specify the sheet index (1) and customize the import by skipping the first row, selecting only the first column, and renaming the column.
- Print the head of the DataFrame.

## Importing SAS File

```python
from sas7bdat import SAS7BDAT

with SAS7BDAT('sales.sas7bdat') as file:
    df_sas = file.to_data_frame()

print(df_sas.head())

pd.DataFrame.hist(df_sas[['P']])
plt.ylabel('count')
plt.show()
```

- Import the SAS7BDAT package.
- Open the SAS file named "sales.sas7bdat" and load it as a DataFrame using the `to_data_frame()` method.
- Print the head of the DataFrame.
- Plot a histogram of the 'P' variable using `pd.DataFrame.hist()` and display the plot.

## Importing Stata Files

```python
import pandas as pd

df = pd.read_stata('disarea.dta')
print(df.head())

pd.DataFrame.hist(df[['disa10']])
plt.xlabel('Extent of disease')
plt.ylabel('Number of countries')
plt.show()
```

- Import the pandas package.
- Specify the file name as "disarea.dta".
- Use `pd.read_stata()` to load the Stata file into a DataFrame.
- Print the head of the DataFrame.
- Plot a

 histogram of the 'disa10' variable using `pd.DataFrame.hist()` and display the plot.

## Importing HDF5 Files

```python
import numpy as np
import h5py

file = 'LIGO_data.hdf5'
data = h5py.File(file, 'r')
print(type(data))

for key in data.keys():
    print(key)
```

- Import the numpy and h5py packages.
- Specify the file name as "LIGO_data.hdf5".
- Load the HDF5 file using `h5py.File()` in read mode ('r').
- Print the datatype of the loaded data.
- Iterate over the keys in the HDF5 file and print them.

## Extracting Data from Your HDF5 File

```python
group = data['strain']

for key in group.keys():
    print(key)

strain = np.array(data['strain']['Strain'])
num_samples = 10000
time = np.arange(0, 1, 1/num_samples)

plt.plot(time, strain[:num_samples])
plt.xlabel('GPS Time (s)')
plt.ylabel('strain')
plt.show()
```

- Access the 'strain' group within the HDF5 file.
- Print the keys of the group.
- Extract the 'Strain' dataset as a NumPy array.
- Set the number of time points to sample as 10,000.
- Create a time vector using `np.arange()`.
- Plot a subset of the 'strain' data against the time vector using Matplotlib.

## Loading MAT Files

```python
import scipy.io

filename = 'albeck_gene_expression.mat'
mat = scipy.io.loadmat(filename)
print(type(mat))
```

- Import the scipy.io package.
- Specify the file name as "albeck_gene_expression.mat".
- Load the MAT file using `scipy.io.loadmat()`.
- Print the datatype of the loaded data.

## The Structure of .MAT in Python

```python
print(mat.keys())
print(type(mat['CYratioCyt']))
print(np.shape(mat['CYratioCyt']))

data = mat['CYratioCyt'][25, 5:]
fig = plt.figure()
plt.plot(data)
plt.xlabel('time (min.)')
plt.ylabel('normalized fluorescence (measure of expression)')
plt.show()
```

- Print the keys of the MATLAB dictionary contained in the MAT file.
- Print the datatype of the value corresponding to the key 'CYratioCyt'.
- Print the shape of the value corresponding to the key 'CYratioCyt'.
- Extract a specific portion of the 'CYratioCyt' data and plot it using Matplotlib.