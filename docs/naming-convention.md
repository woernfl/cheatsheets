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
