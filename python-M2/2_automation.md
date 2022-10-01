## Automation

- first, we need to generate some function that we can use to run repeatedly

```
import requests
from bs4 import BeautifulSoup as soup


def wc_generator():
  url = 'https://news.google.com/rss?h1=en-US&gl=US&ceid=US:en'
  xml_page = requests.get(url).content
  soup_page = soup(xml_page, 'xml')
  news_titles = soup_page.findAll('title')
  wc_string = ""

  for title in news_titles:
    wc_string = wc_string + title.text + " "

  from wordcloud import WordCloud

  wc = WordCloud(background_color = "white", colormap = "Blues", width = 600, height = 400).generate(wc_string)

  import matplotlib.pyplot as plt
  plt.imshow(wc)
  plt.savefig("wordcloud.png")
```

### Importing the `time` library

- we can use a `while` loop to achieve automation
- essentially an infinite loop (be careful!)

```
import time

def automater(func, sec):
  while True:
    func()
    time.sleep(sec)
    
automater(wc_generator, 5)
```

### PyCharm

- use PyCharm IDE - [Download](https://www.jetbrains.com/pycharm/)
- IDEs help programmers make programs
- PyCharm allows us to write more powerful programs


