# SSH

## Basic actions

Connect to a server through a Bastion:

```bash
ssh -t $BASTION_SSH_HOST ssh $FINAL_SSH_HOST
```

Connect using a specific private key:

```bash
ssh -i $PATH_TO_THE_PRIVATE_KEY $USER@$SSH_HOST
```

Skipping the known host check:

```bash
sh -o StrictHostKeyChecking=no $USER@$SSH_HOST
```

Executing cmds via SSH:

```bash
ssh -t $USER@$SSH_HOST $CMD
```

## SSH Keys

### Generation

Generate new SSH Keys:

```bash
ssh-keygen -t rsa -C "$UNIQUE_IDENTIFIER"
```

Press `Enter` to accept default location and then type your paraphrase twice.

2 new files were created in the `~/.ssh` folder, the `id_rsa` and `id_rsa.pub` ones.

### Setting the rights file permissions

Solves `WARNING: UNPROTECTED PRIVATE KEY FILE!`:

```bash
sudo chmod 600 $KEY_PATH
```

### Adding a externally generated key to your ssh-agent

Start the agent and add the key:

```bash
eval $(ssh-agent)
ssh-add ~/.ssh/$KEY_PATH
```
