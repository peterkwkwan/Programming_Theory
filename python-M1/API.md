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

- https://pokeapi.co/api/v2/pokemon/charizard

```
response = requests.get('https://pokeapi.co/api/v2/pokemon/charizard')
print(response)
print(response.content)
```
