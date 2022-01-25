# Curl

## Basic actions

Get a web site:

```bash
curl $WEBSITE_URL
```

Get only the HTTP code back:

```bash
curl --silent -o /dev/null -w "%{http_code}" $WEBSITE_URL
```

Get a web site and specify the host we are reaching from:

```bash
curl -H Host:$WEBSITE_DNS $WEBSITE_IP
```

Follow redirect:

```bash
curl -L -O https://github.com/vim-volt/volt/releases/download/v0.3.7/volt-v0.3.7-linux-amd64
```

Get a binary:

```bash
curl -O $BINARY_URL
```

Get multiple binaries:

```bash
 for i in $(curl -s https://releases.hashicorp.com/terraform/ | grep href | sed 's/.href="//' | cut -d ">" -f2 | cut -d "<" -f1 | grep -E terraform* | cut -d "_" -f2); do curl -O https://releases.hashicorp.com/terraform/$i/terraform_"$i"_linux_amd64.zip; done
```
