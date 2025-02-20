# Naming Convention

## Global Naming Pattern

```
[project]-[env]-[datacenter]-[type]-[purpose]-[number]
```

With the following attributes:

- `project`: project name
- `env`: in which environment are we? `dev` | `tst` | `prd`
- `datacenter`: datacenter in which the server is
- `type`: which kind of ressource? `physical` | `virtual`
- `purpose`: short description of the purpose of this server
    - `app`: application server
    * `bkt`: storage bucket
  * `cfg`: configuration management server
  * `dns`: name server
  * `fwl`: firewall
  * `ftp`: SFTP server
  * `lb`: load balancer server
  * `mon`: monitoring server
  * `pdu`: power distribution unit
  * `prx`: proxy server
  * `rtr`: router
  * `sql`: database server
  * `ssh`: SSH jump/bastion host
  * `sto`: storage server
  * `swt`: switch
  * `ups`: uninterruptible power supply
  * `vcs`: version control software server
  * `vpn`: VPN server
  * `web`: web server
- `number`: unique number

## DNS Naming Pattern

```
[project].[env].[dns_domain]
```

With the following attributes:

- `project`: project name
- `env`: in which environment are we? `dev` | `stage` | `prod`
- `dns_domain`: DNS domain used

## Thanks

Thanks to Stepan for his [blog article](https://stepan.wtf/cloud-naming-convention/) which inspired most of this page.
