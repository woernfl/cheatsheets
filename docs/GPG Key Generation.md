# GPG Key Generation

## Basic actions

- Checking if GPG Key existe:

```bash
gpg --list-secret-keys --keyid-format LONG
```

- GPG key pair generation:

```bash
gpg2 --gen-key
```

```markdown
>:bulb: If you get the following error: `gpg: Sorry, no terminal at all requested - can't get input` remove the line `no-tty` from `~/.gnupg/gpg.conf`
```

- Choose `RSA and RSA` option

- Choose the max lenght size for the key `4096`

- Enter the number of days you want this key to be valid

- Enter ID details

- Type a secure passphrase

- Generate enough entropy

```bash
sudo yum install rng-tools
```

```bash
sudo rngd -r /dev/urandom
```

- Once the key has been generated, list the created keys

```bash
gpg --list-secret-keys --keyid-format LONG
```

- From the list of GPG keys, copy the GPG key ID you'd like to use. In this example, the GPG key ID is `3AA5C34371567BD2`

```bash
$ gpg --list-secret-keys --keyid-format LONG
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot 
ssb   4096R/42B317FD4BA89E7A 2016-03-10
```

- Paste the text below, substituting in the GPG key ID you'd like to use. In this example, the GPG key ID is `3AA5C34371567BD2`

```bash
gpg --armor --export 3AA5C34371567BD2
```

