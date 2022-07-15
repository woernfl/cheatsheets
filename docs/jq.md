# jq

## Basic actions

Get all keys of a json doc:

```bash
cat $JSON_DOC | jq -r '[paths|map(.|tostring)|join(".")]'
```
