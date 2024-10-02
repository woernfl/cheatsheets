# jq

## Basic actions

Get all keys of a json doc:

```bash
cat $PATH_TO_THE_JSON_FILE | jq -r '[paths|map(.|tostring)|join(".")]'
```

Search for a specific value:

```bash
cat $PATH_TO_THE_JSON_FILE | jq '.[] | select(.name=="woernfl")'
```
