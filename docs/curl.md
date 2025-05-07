# Curl

## Basic actions

Get a web site:

```bash
curl $WEBSITE_URL
```

Get all the transactions for a web site:

```bash
curl -v $WEBSITE_URL
```

Get only the HTTP code back:

```bash
curl --silent -o /dev/null -w "%{http_code}" $WEBSITE_URL
```

Continusly check the HTTP code:

```bash
for (( t=1; ; t++ )); do echo "${t}" && curl --silent -o /dev/null -w "%{http_code}" $WEBSITE_URL && sleep 1 && echo ""; done
```

Get a web site and specify the host we are reaching from:

```bash
curl -H Host:$WEBSITE_DNS $WEBSITE_IP
```

Follow redirect:

```bash
curl -L -O $WEBSITE_URL
```

List the content of a remote folder:

```bash
curl --list-only $WEBSITE_URL
```

Also fetching the headers:

```bash
curl -I $WEBSITE_URL
```

Time the request:

```bash
curl  $WEBSITE_URL
```

## Binaries actions

Get a binary:

```bash
curl -O $BINARY_URL
```

Get multiple binaries:

```bash
 for i in $(curl -s https://releases.hashicorp.com/terraform/ | grep href | sed 's/.href="//' | cut -d ">" -f2 | cut -d "<" -f1 | grep -E terraform* | cut -d "_" -f2); do curl -O https://releases.hashicorp.com/terraform/$i/terraform_"$i"_linux_amd64.zip; done
```
