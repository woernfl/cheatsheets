# AWS CDK

## Basic actions

Initialise the code:

```bash
cdk init app --language typescript
```

Bootstrap the AWS account

```bash
cdk bootstrap aws://$AWS_ACCOUNT_ID/$AWS_REGION
```
List the different stacks:

```bash
cdk ls
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

## Environment variables

`CDK_DEFAULT_ACCOUNT`

Specifies an AWS account id to deploy to.

`CDK_DEFAULT_REGION`

Specifies an AWS region to deploy to.
