## HTML WebScrapping

- What is HTML? 
- Intro to HTMl, CSS and Javascript

### Web scrapping the Nike Website
```
# Web scrapping - Nike website
# Prices of all shoes on Nike
# Name of all shoes on Nike
```

#### Steps of web scrapping
```
# Steps of Web Scrapping
# 1) Get the data
# 2) Translate the data
```

### Getting the data
- [Nike Website](https://www.nike.com.hk/?locale=en-gb)

```
import requests

url = 'https://www.nike.com.hk/man/running/shoe/list.htm?intpromo=PNTP'

html_page = requests.get(url).content
```

- our content is in bytes, so we need to translate it

```
# translate the byte content into something python can understand
from bs4 import BeautifulSoup as soup

soup_page = soup(html_page, 'html') # translate the data from a specific language --> in our case, HTML
soup_page
```

- We just want the name of the product and the price of the product
- Using dev tools, we can inspect the page

![image](https://user-images.githubusercontent.com/37263010/191875820-4339e32d-44e3-426c-82c9-99c6e1c8eb5f.png)

```
soup_page.findAll('span') # this will not work! we have too many <span> tags
soup_page.findAll('span', {'class': 'up'}) # can specify the attribute we want!
```

> Now we need to get the name of the shoes. How can we do that?

```
for shoe in shoe_names:
  print(shoe.text)
```

> How do we get the prices?

```
# get the prices
shoe_prices = soup_page.findAll('dd', {'class': 'color666'})

for price in shoe_prices:
  print(price.text)
```

- We have 2 prices though. How can we clean it up?
> Also, how can we print out both the prices and the names at the same time?

- we can use the inspect tool to see the 'box' that contains the shoe item

![image](https://user-images.githubusercontent.com/37263010/191878833-999f4411-8e3f-462c-af21-9eb60a074d2d.png)

```
soup_page.findAll('dl', {'class': 'product_list_content'})[0]
type(shoe_list) # bs4.element.ResultSet
```

- now, we can loop the shoes

```
for shoe in shoe_list:
  # print(type(shoe.findAll('span', {'class', 'up'}))) # bs4.element.ResultSet
  name = shoe.findAll('span', {'class', 'up'})[0] # we need to get the first index since `findAll` returns a ResultSet
  print(title.text)
```

- we can also print out the prices at the same time

```
for shoe in shoe_list:
  # print(type(shoe.findAll('span', {'class', 'up'}))) # bs4.element.ResultSet
  name = shoe.findAll('span', {'class', 'up'})[0].text # we need to get the first index since `findAll` returns a list
  price = shoe.findAll('dd', {'class', 'color666'})[0].text
  print(name)
  print(price)
  print('-'*50)
```

### Translate the data
- Let's now try to turn our data into a DataFrame for analysis

```
# store our names and prices in a list
names = []
prices = []

for shoe in shoe_list:
  names.append(shoe.findAll('span', {'class', 'up'})[0].text)
  prices.append(shoe.findAll('dd', {'class', 'color666'})[0].text)
```

- Let's check the length of our lists are the same

```
# check if all our shoes have prices (and vice-versa)
len(names) == len(prices)
```

- put our names and prices into a Nike `dict`

```
# for easier processing
nike_dict = {
    'Name': names,
    'Price': prices
}

nike_dict
```

> Time to turn our data into a DataFrame! How can we do this? (Hint: pandas)

```
import pandas as pd

nike_df = pd.DataFrame(data=nike_dict)
nike_df
```

> However, before we can start any price analysis, what kind of problems does our data have?

```
# This gives us the wrong answer!
nike_df["Price"].max() # our prices are in string format
```

```
# change our values into integers / floats(prices)
# PROBLEMS: HK, $, commas, double prices

"HK$999".split('HK$') # ['', '999']

"HK$2,299HK$1,839".split('HK$') # ['', '2,299', '1,839']

# we can use -1 index to always get the last value!

# get rid of the commas
"HK$2,299HK$1,839".split('HK$')[-1].replace(',', '')
```

> How can we apply this function on all items in our DataFrame? (Hint: we learned it in M1)

```
nike_df["Price"].apply(lambda x: x.split('HK$')[-1].replace(',', ''))

# update our existing DF 'Price' column
nike_df["Price"] = nike_df["Price"].apply(lambda x: x.split('HK$')[-1].replace(',', ''))

nike_df
```

- Time to plot our data!

```
type(nike_df) # pandas.core.frame.DataFrame
nike_df.plot(kind='bar') # TypeError: no numeric data to plot
```

> We missed one important step (Hint: our data type is wrong!)

```
# convert our type to float
nike_df["Price"] = nike_df["Price"].apply(lambda x: float(x))
nike_df["Price"]
```
![image](https://user-images.githubusercontent.com/37263010/191879297-d365a983-fd69-4be2-8d2b-c4ae39bf8711.png)

```
nike_df.plot(kind="bar")
```
