# AWS CLI

## Basic actions

Enable autocompletion:

```bash
echo "complete -C '$(which aws_completer)' aws" >> ~/.bashrc
```

Create profil config:

```bash
aws configure --profile $PROFILE_NAME
```

```bash
aws sts decode-authorization-message --encoded-message $ENCODED_MESSAGE | jq -r .DecodedMessage | sed 's/\\"/"/g' | jq .
```

## Environment variables

`AWS_ACCESS_KEY_ID`

Specifies an AWS access key associated with an IAM user or role.

`AWS_SECRET_ACCESS_KEY`

Specifies the secret key associated with the access key. This is essentially the "password" for the access key.

`AWS_DEFAULT_REGION`

Specifies the AWS Region to send the request to.

`AWS_PROFILE`

Specifies the name of the CLI profile with the credentials and options to use. This can be the name of a profile stored in a credentials or config file, or the value default to use the default profile. If you specify this environment variable, it overrides the behavior of using the profile named [default] in the configuration file.

`AWS_SHARED_CREDENTIALS_FILE`

Specifies the location of the file that the AWS CLI uses to store access keys (the default is ~/.aws/credentials).

`AWS_CONFIG_FILE`

Specifies the location of the file that the AWS CLI uses to store configuration profiles (the default is ~/.aws/config).
