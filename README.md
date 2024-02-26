# Overeview

## GPT-3.5 Turbo fine-tuning and API updates

## Fine-tuning use cases
Since the release of GPT-3.5 Turbo, developers and businesses have asked for the ability to customize the model to create unique and differentiated experiences for their users. With this launch, developers can now run supervised fine-tuning to make this model perform better for their use cases.

In our private beta, fine-tuning customers have been able to meaningfully improve model performance across common use cases, such as:

- Improved steerability: Fine-tuning allows businesses to make the model follow instructions better, such as making outputs terse or always responding in a given language. For instance, developers can use fine-tuning to ensure that the model always responds in German when prompted to use that language.
- Reliable output formatting: Fine-tuning improves the model's ability to consistently format responses—a crucial aspect for applications demanding a specific response format, such as code completion or composing API calls. A developer can use fine-tuning to more reliably convert user prompts into high-quality JSON snippets that can be used with their own systems.
- Custom tone: Fine-tuning is a great way to hone the qualitative feel of the model output, such as its tone, so it better fits the voice of businesses’ brands. A business with a recognizable brand voice can use fine-tuning for the model to be more consistent with their tone.

## Fient-tuning steps

- Prepare your data
    ```bash
    {
    "messages": [
      { "role": "system", "content": "You are an assistant that occasionally misspells words" },
      { "role": "user", "content": "Tell me a story." },
      { "role": "assistant", "content": "One day a student went to schoool." }
    ]
  }
  ```
    
- Upload files
  ```bash
  curl https://api.openai.com/v1/files \
    -H "Authorization: Bearer $OPENAI_API_KEY" \
    -F "purpose=fine-tune" \
    -F "file=@path_to_your_file"
  ```
  
- Create a fine-tuning job
  ```bash
  curl https://api.openai.com/v1/fine_tuning/jobs \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -d '{
    "training_file": "TRAINING_FILE_ID",
    "model": "gpt-3.5-turbo-0613"
  }'
  ```

- Create a fine-tuning job
  ```bash
 curl https://api.openai.com/v1/chat/completions \
-H "Content-Type: application/json" \
-H "Authorization: Bearer $OPENAI_API_KEY" \
-d '{
  "model": "ft:gpt-3.5-turbo:org_id",
  "messages": [
    {
      "role": "system",
      "content": "You are an assistant that occasionally misspells words"
    },
    {
      "role": "user",
      "content": "Hello! What is fine-tuning?"
    }
  ]
}'

```
 
## reference

- https://platform.openai.com/docs/guides/fine-tuning/create-a-fine-tuned-model
- https://openai.com/blog/gpt-3-5-turbo-fine-tuning-and-api-updates3
- 

