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

#### Basic functions for pandas

```
.read_csv() # reads a CSV into DataFrame

.head() # return the first n rows (default 5)

.tail() # return the last n rows (default 5)

.info() # print out summary of the data plus data types

```

> How do we read a particular column of data?
> Follow up: In dictionaries, how did we access a particular [key:value] pair?

```
ecom["Purchase Price"]

ecom["Purchase Price"].max()
```

> How to get the average?

- Reading error messages --> typo when trying to acccess a column

![image](https://user-images.githubusercontent.com/37263010/189654167-9dcc3b9c-7ec9-46a2-b9dc-efb05c56f839.png)


#### Shortcut for getting all key info at once

```
ecom["Purchase Price"].describe() # get a particular column

ecom.describe() # get all columns with numerical values
```

#### pandas `series`

```
type(ecom["Purchase Price"]) # pandas.core.series.Series
```

- a column of data
- similar to arrays / list


#### 2 primary data structures of pandas
1. `Series` : 1-dimensional
2. `DataFrame` : 2-dimensional
  - As long as there is more than 1 column

#### Applying what we learned to your job

- Using the data, how can we leverage it in a business situation?
- Perhaps we wanted to run some analysis on the highest spenders and create a loyalty program. 
- Demographics, age, address, can all play a part in how we create this program.

> How to retrive the people that paid greater than 80 dollars?

```
ecom["Purchase Price"] > 80 # returns the entire DataFrame with people that have greater than 80 dollars spending

ecom[ecom["Purchase Price"] > 80] # wrapping the "ecom" DataFrame with the above filter
```

- exacting additional info from this filter using what we learned previously

```
vip = ecom[ecom["Purchase Price"] > 80]

vip.shape

vip.min()

vip["CC Provider"]

vip["CC Provider"].unique()

vip["CC Provider"].value_counts() # google 'python pandas unique count values
```

#### Sharing data with colleagues

```
vip.to_csv("some_name")
```

#### Additional assignments

> How many people have the job title of "Lawyer"?

```
ecom.info()

ecom["Job"] == "Lawyer"

lawyers = ecom[ecom["Job"] == "Lawyer"]

lawyers.shape
len(lawyers)
```

> How many different jobs are there in the data set?

```
ecom["Job"].unique()

len(ecom["Job"].unique())
# OR
ecom["Job"].nunique()
```

> How to find the number of each unique job?

```
ecom["Job"].value_counts()
```

> What are the 5 most common Job Titles?

```
ecom["Job"].value_counts().head()
```

> How many people made purchases during morning (AM)? How many purchased in afternoon/evening (PM)?

```
ecom.columns

AM_purchases = ecom[ecom.get("AM or PM") == "AM"]
PM_purchases = ecom[ecom.get("AM or PM") == "PM"]

len(AM_purchases)
len(PM_purchases)
```

> What is the email of the person with the following Credit Card Number: 4926535242672853


```
target_person = ecom[ecom.get("Credit Card") == 4926535242672853]
target_person["Email"]
```
> How many people have American Express as their Credit Card Provider and made a purchase above $95?
```
ecom["CC Provider"].unique()

ecom[ecom["CC Provider"] == "American Express"]


# need to store amex as a variable or else indexing error
# when applying additional filtering, we change the index
amex = ecom[ecom["CC Provider"] == "American Express"] 

amex[amex["Purchase Price"] > 95]
```
- What if we have many filter criteria? Then we have to write lots of variables / lines of code
- `&` symbol comes into play

```
amex_filter = ecom["CC Provider"] == "American Express"
purchase_filter = ecom["Purchase Price"]>95

ecom[(amex_filter) & (purchase_filter)]
```

#### More exercises

> How many people have English ('en') as their Language of choice on the website?

> How many people have an IP Address that has more than 9 digits?

> Someone made a purchase that came from Lot: "90 WT". What was the Purchase Price for this transaction?

## Lambda

- recap of functions

```
# functions
def add10(x):
  return x + 10


add10(50) # 60
```

- a lambda is a function that youcan write with one line of code

```
add20 = lambda x:x+20

add20(20)
```

#### Applying lambda to our data set

```
# 'apply' a function on an entire series

ecom["Job"].apply(len) 

ecom["Purchase Price"].apply(add10)

ecom["Purchase Price"].apply(lambda x:x+50)
```

- `apply` function --> apply your lambda function over the entire series
- lambda function -->  make the changes for an entire column much easier

> How many people have a credit card that expires in 2025?

```
ecom["CC Exp Date"]
```

- Google: "How to separate string in python"

```
ecom["CC Exp Date"].apply(lambda x:x.split('/'))

ecom[ecom["CC Exp Date"].apply(lambda x:x.split('/')[1])=='25'] # use int first (25) to get students to troubleshoot
```

#### When to use apply + lambda?

- When we need to find and manipulate _specific_ information inside each row in a column
