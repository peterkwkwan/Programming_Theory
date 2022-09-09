## Intro to Python

#### What is Programming?
- A way of talking with the computer
- Learning programming === Learning a language
> What are some programming languages?

- How can we get the computer to say "hello" to us?

#### Hello World!
- Machine code

![image](https://user-images.githubusercontent.com/37263010/189385221-60caf7fb-7f2c-4f71-9b4c-d512e27fe5b0.png)

- In C++
- In Java
- In Python


#### Good way to run Python code
- [colab.research.google](https://colab.research.google.com/)
- Web based
- Google docs-like
- Easy to learn

```
hello world
```

![image](https://user-images.githubusercontent.com/37263010/189384839-93333316-421b-4d9e-9b9c-b24db1b274b8.png)

```
print("hello")
type("hello")
type(123)
```


#### 4 steps of programming

1. noun/verb/adj
2. rules for that word

1. type of data --> str/int
2. rules for that data type --> methods / functions

```
"hello world".capitalize()
"hello world".upper()
"hello world".title()
123.upper() // invalid syntax
123 + 10
123 - 10
10 / 2
type(10/2)
'canada'.count() // TypeError: count() takes at least 1 argument (0 given)
'canada'.count('a')
'canada'.count(1) // TypeError: must be str, not int
```

```
'hong kong is very humid'.upper().count('H')
```
> What is the result?

```
x = 'hong kong is very humid'.upper().count('H')
print(x)
```
#### Variables
- container --> a way of storing data


#### 4 steps of programming

1. data types --> str/int
2. methods / functions --> .upper(), .lower(), .count(), print()
3. logic (sentence structure)


```
x > 2
x == 2
x is 2
x is not 2
```

```
if x > 3:
  print ('yay!')
else :
  print ('x is not greater than 3')
```

#### Assignment
- age checker

```
age = 18

if age > 18:
  print('enjoy your beer!')
if age == 18:
  print('drink responsibly!')
else:
  print("sorry you're not allowed alcohol")
```

`int(age) > 18` _vs._ `age = int(input('enter your age'))`

```
int(input('enter your age')) # type casting
```

#### 4 steps of programming

1. data types --> str/int
2. methods / functions --> .upper(), .lower() / print(), type()
3. logic --> if else

- methods are type specific
- methods are 'called' on an object/value/variable
- we cannot invoke a method just by its name

- functions are not associated with any object
- we can invoke a function by just its name

4. libraries
  - analogy: _smartphone_
  - comes pre-packaged with many features
  - however, we have some specific tasks that does not come with the phone
  - download apps / import libraries

#### Assignment
- random lottery generator

```
numbers = list(range(1,50))
print(numbers)

---- 
import random

result = random.sample(numbers, 1)
print(result)
```
