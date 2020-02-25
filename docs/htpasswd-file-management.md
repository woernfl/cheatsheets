# htpasswd file management

## Basic actions

Install nessecary package:

```bash
sudo apt-get install apache2-utils
```

Creates a new file if the file does not exist or modify an existing readable file and stores a record in it for user `admin`:

```bash
htpasswd -c .htpasswd admin
```

Adds or modifies the password for user `admin` in an existing file:

```bash
htpasswd .htpasswd admin
```
