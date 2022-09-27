# Elasticsearch

## Basic actions

Check the health of the cluster:

```bash
curl -u $ELASTIC_USER:$ELASTIC_PASSWORD -XGET "https://$ELASTIC_URL/_cluster/health" | jq
```

List all the indexes:

```bash
curl -u $ELASTIC_USER:$ELASTIC_PASSWORD -XGET "https://$ELASTIC_URL/_cat/indices?v"
```

## Shard Allocations

Check shard allocation issues:

```bash
curl -u $ELASTIC_USER:$ELASTIC_PASSWORD -XGET "https://$ELASTIC_URL/_cluster/allocation/explain?pretty" | jq
```
