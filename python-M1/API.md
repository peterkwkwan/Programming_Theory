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
- [Dad Jokes](https://dadjokes.io/)
- https://dad-jokes.p.rapidapi.com/random/joke

```
response = requests.get('https://dad-jokes.p.rapidapi.com/random/joke')
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
