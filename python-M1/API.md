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
type(JSON_content)
```
