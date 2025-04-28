# Groq API
## Links
* [doc](https://console.groq.com/docs) 
* [models](https://console.groq.com/docs/models)
* [create api key](https://console.groq.com/keys)


## REST api usage
```sh
curl https://api.groq.com/openai/v1/chat/completions -s \
-H "Content-Type: application/json" \
-H "Authorization: Bearer $AI_REST_GROQ" \
-d '{
"model": "llama-3.3-70b-versatile",
"messages": [{
    "role": "user",
    "content": "Explain the importance of fast language models"
}]
}' | jq .
```