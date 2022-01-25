# SSH Keys

## Generation

Generate new SSH Keys:

```bash
ssh-keygen -t rsa -C "$UNIQUE_IDENTIFIER"
```

Press `Enter` to accept default location and then type your paraphrase twice.

2 new files were created in the `~/.ssh` folder, the `id_rsa` and `id_rsa.pub` ones.

## Setting the rights file permissions

Solves `WARNING: UNPROTECTED PRIVATE KEY FILE!`:

```bash
sudo chmod 600 $KEY_PATH
```

## Adding a externally generated key to your ssh-agent

Start the agent and add the key:

```bash
eval $(ssh-agent)
ssh-add ~/.ssh/$KEY_PATH
```
