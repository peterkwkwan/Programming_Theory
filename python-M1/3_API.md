# API
- Application Programming Interface


#### What is an API?
- Messenger between 2 computers
- E.g. Waiters at a restaurant (McDonald's ordering machine)

#### Using APIs

- HKMA (https://apidocs.hkma.gov.hk/)

```
import requests

response.get(requests.get('https://api.hkma.gov.hk/public/bank-svf-info/register-ais-lros?lang=en')
```

> What do we get? What is Response 200 mean?

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
import json

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
![image](https://user-images.githubusercontent.com/37263010/193386355-afc1087c-45a3-4a5c-a32f-b4b3883eea30.png)

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


```
for country in countries:
  if country.get('borders') != None:
    print(country['borders'])
```

