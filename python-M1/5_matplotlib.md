## Matplotlib

- excellent 2-D & 3-D plotting library for visualizing data
- Features:
  - easy-to-use
  - support for custom labels and texts
  - high level of control over every element in a plot figure
  - outputs in many different formats
  - customizable
  
#### Installiation and usage
```
pip install matplotlib
 
-----

import matplotlib as plt
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

```
plt.axis([-50, 80, 3, 8])
plt.plot(a,b)
```
![image](https://user-images.githubusercontent.com/37263010/191670659-459dc9e6-1454-44ba-b067-2066dd577b06.png)

