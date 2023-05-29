# Python
Python shell is a place to write code and get immediate results.
Python scripts are simply text files  with extension .py consisting of Python commands that are executed.
 `print` command is used to print contents/output from scripts.
 
### Variable
 a specific case-sensitive name used to store/named memory locations. Call up a variable value through variable name.

### DataTypes
`type()` is used to find to find the datatype of  a token.[function]
**float** - real numbers
**int** - integers
**str** - string, text
**bool** - True, False

## Lists
- **[ ]**
- A list is a name given to a collection of values(any typ, even lists)
- Lists contain the references of the stored values
- when you copy a list and alter it, it affects the original list
- use `list()` or slicing to select values to copy

### Subsetting lists
`list_name[index]` indices start from 0(zero indexing)
- Negative indexing lets you select from the end

### Slicing
-allows to select multiple values in list
`list_name[start:end]` start-inclusive, end- exclusive
a[:5] - from start to 5
a[2:] - from index 2 to end of the list

### Manipulating Lists
- list_name[index] = value
- slicing can be used for manipulation
- old_list+[values] = new_list
- `del(list_name[index])`

## Functions
-Piece of reusable code
**Example** (Self Explanatory)
`max()`
`len()`
`round(_number,_digits)`
`round(_number)`
`help(functn_name)` 

### Methods
- functions that belong to objects
- **Example** 
- `list_name.index(index)`
- `list_name.count(value)`
- `list_name.append(value)` some methods change the objects that call them
- `string_value.capitalize()`
- `string_value.replace(original,To_be_replaced_with)`

## Packages
Each script is a module consisting of functions, methods , objects etc
Related modules are stored in packages
**To Install Packages**
```python 
python3 get-pip.py
pip3 install <package_name>

#To use a package it ha sto be imported first
import <package_name>

#using alias
import <package_name> as <alias>

#To import specific parts
from <package_name> import <part_name>
```

**Example**
```python 
#import <package_name>
import numpy 

#using alias
import numpy as np

#To import specific parts
from numpy import array

#most preferable
import numpy as np
np.array()
```