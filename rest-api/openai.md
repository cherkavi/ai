# Open AI REST API 

## Links
* [api reference](https://platform.openai.com/docs/api-reference/introduction)
* [docs](https://platform.openai.com/docs)
* [key generator](https://platform.openai.com/api-keys)
* [control api usage/cost](https://platform.openai.com/usage)
* [guide agents](https://platform.openai.com/docs/guides/agents)
  ```bash 
  pip install openai-agents
  ```

## Steps
1. create new secret key and put it in your env
```sh
x-www-browser https://platform.openai.com/api-keys
export AI_REST_OPENAI=sk-.....
```
2. obtain list of models
```sh
curl  -H "Authorization: Bearer $AI_REST_OPENAI" -H "Content-Type: application/json" \
https://api.openai.com/v1/models
```
3. make your request
```sh
curl https://api.openai.com/v1/chat/completions \
-H "Authorization: Bearer $AI_REST_OPENAI" -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-3.5-turbo",
    "messages": [
      {
        "role": "user",
        "content": "Hello, who are you?"
      }
    ]
  }'
```
```python
import requests
import os
# Set your API key here
api_key = os.environ.get['AI_REST_OPENAI']

# Define the endpoint
url = 'https://api.openai.com/v1/chat/completions'

# Set up the headers
headers = {
    'Authorization': f'Bearer {api_key}',
    'Content-Type': 'application/json',
}

# Define the data payload
data = {
    "model": "gpt-3.5-turbo",  # Specify the model you want to use
    "messages": [
        {"role": "user", "content": "Hello, how can AI help me today?"}
    ],
    "max_tokens": 150  # Limit the response length
}

# Make the POST request
response = requests.post(url, headers=headers, json=data)

# Check the response
if response.status_code == 200:
    response_data = response.json()
    print("AI Response:", response_data['choices'][0]['message']['content'])
else:
    print("Error:", response.status_code, response.text)

```