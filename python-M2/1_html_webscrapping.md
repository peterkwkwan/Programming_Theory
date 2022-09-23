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
len(names) == len(prices)
```
