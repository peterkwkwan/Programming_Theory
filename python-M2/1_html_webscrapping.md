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

![image](https://user-images.githubusercontent.com/37263010/191875820-4339e32d-44e3-426c-82c9-99c6e1c8eb5f.png)
