# Study Notes: Creating a Database Engine

In this study guide, we will cover the basics of creating a database engine using SQLAlchemy in Python. We will explore various operations such as retrieving table names, executing SQL queries, filtering records, ordering results, and joining tables.

## Setting up the Database Engine

To begin, we need to import the necessary packages and create an engine object to connect to the database. In this example, we will use a SQLite database named Chinook.

```python
from sqlalchemy import create_engine

engine = create_engine('sqlite:///Chinook.sqlite')
```

## Retrieving Table Names

We can retrieve the names of the tables present in the database using the `table_names()` method of the engine object. This will give us a list of table names.

```python
table_names = engine.table_names()
print(table_names)
```

## Executing a Basic SQL Query

To execute a basic SQL query and retrieve the results, we can use the `execute()` method of the database connection. In the example below, we select all rows from the "ALBUM" table and store the results in a Pandas DataFrame.

```python
from sqlalchemy import create_engine
import pandas as pd

engine = create_engine('sqlite:///Chinook.sqlite')

# Open engine connection
con = engine.connect()

# Perform query
rs = con.execute("SELECT * FROM ALBUM")

# Save results to DataFrame
df = pd.DataFrame(rs.fetchall())

# Close connection
con.close()

# Print the head of the DataFrame
print(df.head())
```

## Customizing the SQL Query Results

We can further customize the SQL query results by specifying the columns we want to retrieve and limiting the number of records. In the example below, we select only the "LastName" and "Title" columns from the "Employee" table and limit the results to three rows.

```python
with engine.connect() as con:
    rs = con.execute("SELECT LastName, Title FROM Employee")
    df = pd.DataFrame(rs.fetchmany(size=3))
    df.columns = rs.keys()

print(len(df))
print(df.head())
```

## Filtering Records with WHERE Clause

We can filter the records in the database using the SQL WHERE clause. In the example below, we select all rows from the "Employee" table where the "EmployeeId" is greater than or equal to 6.

```python
with engine.connect() as con:
    rs = con.execute("SELECT * FROM Employee WHERE EmployeeId >= 6")
    df = pd.DataFrame(rs.fetchall())
    df.columns = rs.keys()

print(df.head())
```

## Ordering Records with ORDER BY Clause

To order the records in the result set, we can use the SQL ORDER BY clause. In the example below, we select all rows from the "Employee" table and order them by the "BirthDate" column in ascending order.

```python
with engine.connect() as con:
    rs = con.execute("SELECT * FROM Employee ORDER BY BirthDate ASC")
    df = pd.DataFrame(rs.fetchall())
    df.columns = rs.keys()

print(df.head())
```

## Executing SQL Queries with Pandas

Instead of using the execute method, we can directly execute SQL queries and store the results in a DataFrame using Pandas' `read_sql_query()` function. This provides a more concise way of retrieving data from the database.

```python
from sqlalchemy import create_engine
import pandas as pd

engine = create_engine('sqlite:///Chinook.sqlite')

# Execute query and store records in DataFrame
df = pd.read_sql_query("SELECT * FROM ALBUM", engine)

print(df.head())

# Open engine in context manager and store query result in df1
with engine.connect() as con:
    rs = con.execute("SELECT * FROM Album")
    df1 = pd.DataFrame(rs.fetchall())
    df1.columns = rs.keys()

# Confirm that both methods yield the same result
print(df.equals(df1))
```

## Joining Tables

To join multiple tables in a database, we can use the SQL JOIN operation. In the example below, we join the "Album" and "Artist" tables on the "ArtistID" column and retrieve the "Title" and "Name" columns.

```python
with engine.connect() as con:
    df = pd.read_sql_query("SELECT Title, Name FROM Album INNER JOIN Artist ON Album.ArtistID = Artist.ArtistID", engine)
    
print(df.head())
```

