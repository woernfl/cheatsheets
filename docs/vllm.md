# VLLM

## Basic actions

### Ask a question

```bash
curl -X POST https://$VLLM_API_URL/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "model": "RedHatAI/DeepSeek-R1-Distill-Llama-70B-quantized.w8a8",
    "messages": [
      {"role": "system", "content": "You are a helpful assistant."},
      {"role": "user", "content": "Explain the theory of relativity in one sentence."}
    ],
    "max_tokens": 4092,
    "temperature": 0.7
  }'
```
