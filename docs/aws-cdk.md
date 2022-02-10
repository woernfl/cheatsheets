# AWS CLI

## Basic actions

Initialise the code:

```bash
cdk init app --language typescript
```

Bootstrap the AWS account

```bash
cdk bootstrap aws://$AWS_ACCOUNT_ID/$AWS_REGION
```

See what the Cloudformation template will look like:

```bash
cdk synth
```

Check the diff between what is currently deployed and what is currently declared in the code:

```bash
cdk diff
```

Deploy the stack

```bash
cdk deploy
```

Destroy the stack

```bash
cdk destroy
```
