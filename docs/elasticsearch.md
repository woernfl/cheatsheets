# Elasticsearch

## Shard Allocations

Check shard allocation issues:

```bash
curl -u $ELASTIC_USER:ELASTIC_PASSWORD -XGET "https://$ELASTIC_URL/_cluster/allocation/explain?pretty" | jq
```
