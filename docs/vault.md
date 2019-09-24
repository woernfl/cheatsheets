# Hashicorp Vault

## Token managment

Create a token using LDAP auth:

```bash
TOKEN=$(curl --data "{\"password\":\"$password\"}" "$VAULT_ADDR/v1/auth/ldap/login/$username" | jq -r '.auth.client_token')
```

Self renew a token:

```bash
curl --header "X-Vault-Token: $TOKEN" --request POST --data "{\"increment\": \"100h\"}" $VAULT_ADDR/v1/auth/token/renew-self
```

## Secrets managment

Retrive secret from Vault:

```bash
curl --silent -H "X-Vault-Token: $TOKEN" $VAULT_ADDR/v1/secret/data/$SECRET_PATH | jq
```

Writting a secret to Vault:

```bash
curl -H "X-Vault-Token: $TOKEN" -H "Content-Type: application/json" -X POST -d '{"value":"bar"}' $VAULT_ADDR/v1/$SECRET_PATH
```
