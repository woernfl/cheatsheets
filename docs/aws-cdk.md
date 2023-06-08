# AWS CDK

## Basic actions

Install or update the CDK cli:

```bash
sudo npm install -g aws-cdk@latest
```

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
cdk synth $STACK_NAME
```

Check the diff between what is currently deployed and what is currently declared in the code:

```bash
cdk diff $STACK_NAME
```

Deploy the stack

```bash
cdk deploy $STACK_NAME
```

Destroy the stack

```bash
cdk destroy $STACK_NAME
```

## Environment variables

`CDK_DEFAULT_ACCOUNT`

Specifies an AWS account id to deploy to.

`CDK_DEFAULT_REGION`

Specifies an AWS region to deploy to.
