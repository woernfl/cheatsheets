# Curl

## Basic actions

Get a web site:

```bash
curl $WEBSITE_URL
```

Get a web site and specify the host we are reaching from:

```bash
curl -H Host:$WEBSITE_DNS $WEBSITE_IP
```
