# API
- Application Programming Interface


#### What is an API?
- Messenger between 2 computers
- E.g. Waiters at a restaurant (McDonald's ordering machine)

#### Using APIs

```
import requests
import json
```
- [Game of Thrones API](https://thronesapi.com/)
- https://thronesapi.com/api/v2/Characters

```
response = requests.get('https://thronesapi.com/api/v2/Characters')
print(response)
content = response.content
print(content)
```

- Whats the data type?

```
type(content) // bytes
```

- JSON --> Javascript Object Notation
- `import json` --> translator! (translation library)
- transforms byte data into python readable data

```
JSON_content = json.loads(content)
JSON_content
type(JSON_content) // list
```

#### Accessing the list via index
```
JSON_content[1]
type(JSON_content[0]) // dictionary
# dict --> key:value pairs
```

```
first_item = JSON_content[0]
first_item['firstName']
first_item.get('firstName')
```

```
first_item.keys()
keys = first_item.keys()
type(keys) // dict_keys
```

#### Nested dict, lists
- https://restcountries.com/v3.1/all

```
countries_response = requests.get('https://restcountries.com/v3.1/all')
countries_response
```

```
countries_content = countries_response.content
JSON_countries = json.loads(countries_content)

JSON_countries[0]
```

```
JSON_countries[0]['borders'] --> nested list
```

```
borders = JSON_countries[0]['borders']
type(borders)
```

#### How to print out all the borders 1 by 1?
- for loop

```
for border in borders:
  print(border)
```

#### How to access nested object?
- `'swe': {'official': 'Republiken Finland', 'common': 'Finland'}}},`

```
finland_dict['name']['nativeName'].get('swe')['official']
```

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

