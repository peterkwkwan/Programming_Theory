## Matplotlib

- excellent 2-D & 3-D plotting library for visualizing data
- Features:
  - easy-to-use
  - support for custom labels and texts
  - high level of control over every element in a plot figure
  - outputs in many different formats
  - customizable
  
#### Installation and usage
```
pip3 install matplotlib # in terminal (for jupyter notebook)

import matplotlib.pyplot as plt
-----
```

- below line is needed for jupyter notebooks
```
%matplotlib inline
```

### Generating a plot chart

```
x = list(range(0, 10))
y = list(range(-10, 0))

plt.plot(x, y)
```

```
a = [0, -100, 25, 67, -345]
b = [0, 3, 7, 3, 9] 
plt.plot(a,b)
```
![image](https://user-images.githubusercontent.com/37263010/191670645-f3c76669-53e3-4b18-be25-690003595121.png)


> What if we wanted to just focus on a specific area of the chart?
- we can set specific [start,end] points for our graph 
- `axis([xmin, xmax, ymin, ymax])` [reference - official docs](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.axis.html)
```
plt.axis([-50, 80, 3, 8])
plt.plot(a,b)
```
![image](https://user-images.githubusercontent.com/37263010/191670659-459dc9e6-1454-44ba-b067-2066dd577b06.png)

> What if we wanted to name our chart and label the axis?

```
plt.title("Triangle")
plt.xlabel("Array A")
plt.ylabel("Array B")
plt.plot(a,b)
```

- We can also rename our axis 'tick' indicators

```
plt.xticks((-40, -20, 0, 20, 40, 60, 80), ('Hello', 'World', 'this', 'graph', 'is', 'totally', 'awesome'))
```

- coloring the graph
```
plt.plot(a,b, color='red')
```

### Histogram (bar charts)
```
plt.hist(a)
```
![image](https://user-images.githubusercontent.com/37263010/191672153-1c0710f4-e822-44f1-83cd-7d3cc19ef05a.png)

### Plotting trends using PyTrends

#### Installation and usage

- Unofficial API for Google Trends
- API interface for automating downloading of reports from Google Trends

```
pip3 install pytrends # in terminal (for jupyter notebook)

!pip install pytrends # in Google Colab
```

```
from pytrends.request import TrendReq

# Create pytrends object and request data from Google
pytrends = TrendReq(hl='en-US') # hl = host language

# extract data about certain keywords
keywords = ['Python', 'C++', 'Java', 'HTML', 'Javascript']

# specify the words and timeframe
pytrends.build_payload(keywords, timeframe='today 5-y')
data = pytrends.interest_over_time()
data
```
