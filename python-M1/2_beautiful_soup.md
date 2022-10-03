
## XML Web Scraping

- Extensible Markup Language
- Web scraping is the process of using bots to extract content and data from a website.

- [Google News](news.google.com)
- https://news.google.com/rss


```
news_url = 'https://news.google.com/rss'

import requests

requests.get(news_url)
```

- Beautiful Soup: make XML pretty (library)

```
from bs4 import BeautifulSoup
from urllib.request import urlopen

xml_page = urlopen(news_url).read()

type(xml_page)
```

```
soup_page = BeautifulSoup(xml_page, 'xml')
```

- find the news title, news website, news publication page

```
news_list = soup_page.findAll('item')
news_list

```

- loop through all the items

```
for item in news_list:
  print(item.title.text)
  print(item.pubDate.text)
  
# accessing individual items
news_list[0].title.text

# check data type
type(news_list[0].title.text)
```
