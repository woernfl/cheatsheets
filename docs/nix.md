# Nix

## Basic actions

Config file path:

```bash
/etc/nixos/configuration.nix
```

## Add some packages

```bash
nixpkgs.config = {

    allowUnfree = true;

    chromium = {};

  };

environment.systemPackages = [ pkgs.chromium ];
```

Then reload the config:

```bash
sudo nixos-rebuild switch
```
