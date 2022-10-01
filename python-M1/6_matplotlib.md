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
plt.show() # only for jupyter notebooks
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
![image](https://user-images.githubusercontent.com/37263010/191680329-a82cd486-6953-4fe0-9c5f-37bffdebf507.png)

> How can we visualize this better? We can use the knowledge we got from `matplotlib`!

```
plt.plot(data)
```

![image](https://user-images.githubusercontent.com/37263010/191680883-73ecb8ba-0f74-43f2-87fb-b6143a90216b.png)

- Add a legend

```
plt.plot(data)
plt.legend(keywords, loc="upper left")
```

#### Putting it all together

```
plt.plot(data)
plt.legend(keywords, loc="upper left")
plt.suptitle('Programming language searches on Google')
plt.xlabel('Years')
plt.ylabel('Weekly searches')
plt.savefig('data.png')
```
![image](https://user-images.githubusercontent.com/37263010/191722351-31f2806f-fe14-4fbe-9405-559602c7ec94.png)

### Analyzing data points

```
focus = ['Python', 'Java']
plt.plot(data[focus])
plt.legend(focus, loc="upper left")
```

#### Country-level data about our keywords

```
# Country level data filter
data2 = pytrends.interest_by_region(resolution='COUNTRY', inc_low_vol=True)

# Filter by 'Python' keyword and get the 10 highest results
data2 = data2['Python'].nlargest(10)
plt.plot(data2)
```
![image](https://user-images.githubusercontent.com/37263010/191740337-b55f7597-a50c-49c4-8515-b2cdf78db1b2.png)

- check our type

```
type(data2) # pandas.core.series.Series
```
- convert it to DataFrame
- pandas is much better for bar chart instead of matplotlib 

```
import pandas as pd
# convert to DataFrame
if not isinstance(data2, pd.DataFrame): 
  data2 = data2.to_frame()
type(data2) # pandas.core.frame.DataFrame
```

```
# use pandas for bar chart instead of matplotlib 
data2.plot(kind="bar")
```
![image](https://user-images.githubusercontent.com/37263010/191740714-69cdac46-5c7c-41c8-bca5-37ab539b8fa6.png)

- we can still continue to use matplotlib for additional labels
```
# use matplotlib to add titles
plt.suptitle('python searches by country')
plt.xlabel('Countries')
plt.ylabel('Averages number of searches over 5 years')
```

### Plot a bar chart including all keywords/programming languages

```
# plot a bar chart with multiple keywords
data3 = pytrends.interest_by_region(resolution='COUNTRY', inc_low_vol=True)
data3 = data3[55:60]
data3 
```
![image](https://user-images.githubusercontent.com/37263010/191742485-92208d86-a793-4fe2-9dbc-0e0f15a20358.png)

```
data3.plot(kind="bar")
```

![image](https://user-images.githubusercontent.com/37263010/191742673-4337b528-a39a-42e6-ae9c-61fdac87cc66.png)
