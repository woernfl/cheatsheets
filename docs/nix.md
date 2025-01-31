# Nix

## ## Add some packages

Config file path:

```bash
/etc/nixos/configuration.nix
```

Add the chromimum package

```bash
environment.systemPackages = [ pkgs.chromium ];
```

Then reload the config:

```bash
sudo nixos-rebuild switch
```

Here is the [list of packages](https://search.nixos.org/packages).
