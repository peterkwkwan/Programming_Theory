## Pandas
- key cornerstone of data science
- stands for "panel data"
  - panel = tabular data / spreadsheet / excels / tables

- [Meet the man behind the most important tool in data science](https://qz.com/1126615/the-story-of-the-most-important-tool-in-data-science/)
- [pandas documentation](https://pandas.pydata.org/)

#### Problems that pandas solves
- Python has limitations & constraints
- What pandas brings to the table
  1. Importing CSV files
  2. Dealing with tabular/spreadsheet-like data
  3. Makes analyzing data much simpler

#### Fetching data and playing with pandas

- We can import our own custom `.csv`, excel files
- [Pokemon CSV](https://gist.github.com/armgilles/194bcff35001e7eb53a2a8b441e8b2c6)

```
pd.read_csv('/pokemon.csv')
```

- Git clone some pre-made table data
```
!git clone https://github.com/PrefaceCoding/M1L5
```

![image](https://user-images.githubusercontent.com/37263010/189575531-b2eb7576-5a78-4728-a7a2-43fe1f20d4c7.png)

> How do we import Python packages?

```
import pandas as pd
ecom = pd.read_csv('/content/M1L5/Ecommerce Purchases.dms')

type(ecom)
```

#### Crucial functions for pandas

```
.read_csv() # reads a CSV into DataFrame

.head() # return the first n rows (default 5)

.tail() # return the last n rows (default 5)

.info() # print out summary of the data plus data types

.describe() #
```

> How do we read a particular column of data?
> Follow up: In dictionaries, how did we access a particular [key:value] pair?

```
ecom["Purchase Price"]

ecom["Purchase Price"].mean()
```

- Reading error messages --> typo when trying to acccess a column

![image](https://user-images.githubusercontent.com/37263010/189654167-9dcc3b9c-7ec9-46a2-b9dc-efb05c56f839.png)



#### 2 primary data structures of pandas
1. `Series` : 1-dimensional
2. `DataFrame` : 2-dimensional

