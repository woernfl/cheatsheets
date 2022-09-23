# Elasticsearch

## Basic actions

Check the health of the cluster:

```bash
curl -u $ELASTIC_USER:$ELASTIC_PASSWORD -XGET "https://$ELASTIC_URL/_cluster/health"
```

## Shard Allocations

Check shard allocation issues:

```bash
curl -u $ELASTIC_USER:$ELASTIC_PASSWORD -XGET "https://$ELASTIC_URL/_cluster/allocation/explain?pretty" | jq
```
