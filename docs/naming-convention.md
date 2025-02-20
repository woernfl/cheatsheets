# Naming Convention

## Global Naming Pattern

```
[owner]-[project]-[env]-[resource]-[location]-[description]-[suffix]
```

With the following attributes

- `owner`: who ones the ressource? Typically a personne or a group of personne.
- `project`: by whom is the ressource used?
- `env`: in which environment are we? `dev` | `stage` | `prod`
- `ressource`: what ressource type is it? `compute` | `k8s` | `bucket` | `...`
- `location`: where is the ressource located? In a region? In a AZ?
- `description`: What is the aim of the ressource?
- `suffix`: random suffix to differenciate the ressource from other similar one and make sure uniqueness is achieved

## Server Naming Pattern

```
[datacenter]-[type]-[purpose]-[number]
```

With the following attributes:

- `datacenter`: datacenter in which the server is
- `type`: which kind of server? `physical` | `virtual`
- `purpose`: short description of the purpose of this server
  - `app`: application server
  - `cfg`: configuration management server
  - `dns`: name server
  - `fwl`: firewall
  - `ftp`: SFTP server
  - `lb`: load balancer server
  - `mon`: monitoring server
  - `pdu`: power distribution unit
  - `prx`: proxy server
  - `rtr`: router
  - `sql`: database server
  - `ssh`: SSH jump/bastion host
  - `sto`: storage server
  - `swt`: switch
  - `ups`: uninterruptible power supply
  - `vcs`: version control software server
  - `vpn`: VPN server
  - `web`: web server
- `number`: unique number

## DNS Naming Pattern

```
[project].[env].[dns_domain]
```

With the following attributes:

- `project`: by whom is the ressource used?
- `env`: in which environment are we? `dev` | `stage` | `prod`
- `dns_domain`: DNS domain used

## Thanks

Thanks to Stepan for his [blog article](https://stepan.wtf/cloud-naming-convention/) which inspired most of this page.
