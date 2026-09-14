# API Practice for JSON Reading and Testing

This folder is meant for practicing with real-world public APIs that return JSON. The goal is to help you:

- read JSON responses from public APIs
- inspect nested data structures
- write clean test cases for API behavior
- validate status codes, response shapes, and field values

## Recommended Public APIs

These are widely used and open for practice:

1. JSONPlaceholder
   - URL: https://jsonplaceholder.typicode.com
   - Best for: beginner API practice, CRUD-style endpoints, nested JSON
   - Example endpoints:
     - GET /posts
     - GET /posts/1
     - GET /users/1
     - GET /todos?userId=1

2. ReqRes
   - URL: https://reqres.in
   - Best for: users and authentication-like flows
   - Example endpoints:
     - GET /api/users
     - GET /api/users/2
     - POST /api/users

3. GitHub REST API
   - URL: https://api.github.com
   - Best for: real-world JSON, metadata, pagination, nested fields
   - Example endpoints:
     - GET /repos/microsoft/vscode
     - GET /repos/microsoft/vscode/issues
     - GET /users/octocat

4. Open-Meteo
   - URL: https://api.open-meteo.com
   - Best for: weather JSON, query parameters, handling time-series data
   - Example endpoints:
     - GET /v1/forecast?latitude=12.97&longitude=77.59&current=temperature_2m

5. REST Countries
   - URL: https://restcountries.com
   - Best for: country data, arrays, nested region/subregion data
   - Example endpoints:
     - GET /v3.1/all
     - GET /v3.1/name/india

6. PokeAPI
   - URL: https://pokeapi.co/api/v2
   - Best for: list endpoints and nested object exploration
   - Example endpoints:
     - GET /pokemon/ditto
     - GET /pokemon?limit=10

7. SWAPI (Star Wars API)
   - URL: https://swapi.py4e.com/api
   - Best for: real-world JSON arrays and nested resources
   - Example endpoints:
     - GET /people/1
     - GET /films

8. Dog CEO API
   - URL: https://dog.ceo/api
   - Best for: image URLs, message fields, random data
   - Example endpoints:
     - GET /breeds/list/all
     - GET /breeds/image/random

## Best APIs for Your Level

### Beginner level
- JSONPlaceholder
- ReqRes
- Dog CEO API

### Intermediate level
- Open-Meteo
- REST Countries
- PokeAPI

### Advanced level
- GitHub REST API
- SWAPI

## Python Setup

Install the required packages:

```bash
pip install requests pytest
```

## Basic JSON Reading Example

```python
import requests

response = requests.get('https://jsonplaceholder.typicode.com/posts/1', timeout=10)
response.raise_for_status()

post = response.json()
print(post['title'])
print(post['body'])
```

## Practice Tasks

### Task 1: Read JSON from a public API
Write a script that:

- calls `https://jsonplaceholder.typicode.com/posts/1`
- reads the JSON response
- prints `userId`, `id`, `title`, and `body`

Expected output:
- a Python dictionary
- keys like `userId`, `id`, `title`, `body`

### Task 2: Count items in an array
Write a script that:

- calls `https://jsonplaceholder.typicode.com/comments`
- counts how many comments are returned
- prints the total count

### Task 3: Filter data by a condition
Write a script that:

- calls `https://jsonplaceholder.typicode.com/posts`
- filters posts where `userId == 1`
- prints the filtered list

### Task 4: Read nested JSON fields
Write a script that:

- calls `https://reqres.in/api/users/2`
- reads nested fields like `data.first_name`, `data.last_name`, `support.url`

### Task 5: Parse weather JSON
Write a script that:

- calls Open-Meteo weather API
- reads `current.temperature_2m`, `current.time`, and `timezone`

### Task 6: Read GitHub metadata
Write a script that:

- calls `https://api.github.com/repos/microsoft/vscode`
- prints `full_name`, `stargazers_count`, `open_issues_count`, `default_branch`

## API Test Cases You Should Write

Below are practical test cases you can write in `pytest`.

### Test Case 1: JSONPlaceholder posts endpoint returns JSON array

```python
import requests

BASE_URL = 'https://jsonplaceholder.typicode.com'


def test_get_posts_returns_list():
    response = requests.get(f'{BASE_URL}/posts', timeout=10)
    assert response.status_code == 200

    data = response.json()
    assert isinstance(data, list)
    assert len(data) > 0

    first_post = data[0]
    assert set(['userId', 'id', 'title', 'body']).issubset(first_post.keys())
```

### Test Case 2: Reading a single post

```python
import requests

BASE_URL = 'https://jsonplaceholder.typicode.com'


def test_get_single_post():
    response = requests.get(f'{BASE_URL}/posts/1', timeout=10)
    assert response.status_code == 200

    post = response.json()
    assert post['id'] == 1
    assert post['userId'] == 1
    assert isinstance(post['title'], str)
    assert isinstance(post['body'], str)
```

### Test Case 3: User endpoint returns nested JSON data

```python
import requests

BASE_URL = 'https://reqres.in/api'


def test_get_user_returns_nested_data():
    response = requests.get(f'{BASE_URL}/users/2', timeout=10)
    assert response.status_code == 200

    data = response.json()
    assert data['data']['id'] == 2
    assert data['data']['email'].endswith('@reqres.in')
    assert data['support']['url']
```

### Test Case 4: Missing resource returns 404

```python
import requests

BASE_URL = 'https://jsonplaceholder.typicode.com'


def test_get_missing_post_returns_404():
    response = requests.get(f'{BASE_URL}/posts/999999', timeout=10)
    assert response.status_code == 404
```

### Test Case 5: Weather API returns expected JSON structure

```python
import requests


def test_open_meteo_weather_response():
    url = (
        'https://api.open-meteo.com/v1/forecast'
        '?latitude=12.97&longitude=77.59'
        '&current=temperature_2m,wind_speed_10m'
    )

    response = requests.get(url, timeout=10)
    assert response.status_code == 200

    data = response.json()
    assert 'current' in data
    assert 'temperature_2m' in data['current']
    assert 'timezone' in data
```

### Test Case 6: GitHub repo API returns real metadata

```python
import requests


def test_github_repo_metadata():
    response = requests.get('https://api.github.com/repos/microsoft/vscode', timeout=10)
    assert response.status_code == 200

    data = response.json()
    assert data['full_name'] == 'microsoft/vscode'
    assert isinstance(data['stargazers_count'], int)
    assert isinstance(data['open_issues_count'], int)
    assert isinstance(data['default_branch'], str)
```

### Test Case 7: REST Countries returns a list for all countries

```python
import requests


def test_rest_countries_all_returns_list():
    response = requests.get('https://restcountries.com/v3.1/all', timeout=10)
    assert response.status_code == 200

    data = response.json()
    assert isinstance(data, list)
    assert len(data) > 0

    first_country = data[0]
    assert 'name' in first_country
    assert 'cca2' in first_country
```

### Test Case 8: PokeAPI returns expected object fields

```python
import requests


def test_pokeapi_ditto_returns_expected_fields():
    response = requests.get('https://pokeapi.co/api/v2/pokemon/ditto', timeout=10)
    assert response.status_code == 200

    data = response.json()
    assert data['name'] == 'ditto'
    assert isinstance(data['id'], int)
    assert isinstance(data['sprites'], dict)
```

## Suggested Practice Roadmap

### Week 1
- JSONPlaceholder: posts, users, comments
- basic JSON reading using `requests`
- write simple `pytest` tests

### Week 2
- ReqRes: nested JSON and user data
- Open-Meteo: query parameters and returned values
- REST Countries: arrays, filtering, and nested objects

### Week 3
- GitHub API: real-world metadata and pagination
- PokeAPI and SWAPI: list endpoints and detailed records

## Good Test Writing Habits

- always check `response.status_code`
- convert JSON with `response.json()` before asserting
- validate both structure and values
- use `assert isinstance(..., list)` for arrays
- use `assert 'key' in data` for nested JSON checks
- test both success and failure cases

## Extra Challenges

Try writing tests for:

1. pagination in GitHub issues or users endpoints
2. filtering countries by region
3. verifying `support.url` exists for ReqRes users
4. checking that weather data has `current.temperature_2m`
5. verifying the number of returned posts is greater than zero
6. handling invalid latitude/longitude values gracefully

## Bonus: Real-World Interview-Style Questions

1. What is the difference between `response.json()` and printing raw text?
2. How do you validate that the API always returns a JSON object?
3. How do you handle APIs that return 429 Too Many Requests?
4. How do you test an endpoint that requires query parameters?
5. How do you write a test that ensures all required keys are present?

## Quick Tips

- Use `requests.get(..., timeout=10)` to avoid hanging requests.
- Use `raise_for_status()` for faster debugging.
- Prefer `pytest` for clean assertions.
- For public APIs, always respect rate limits.

## Next Step

Open the JSON sandbox folder in this workspace and start by solving the file-based JSON tasks there. Then move to these API-based exercises to practice real JSON data handling and testing.
