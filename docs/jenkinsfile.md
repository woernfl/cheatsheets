# Jenkinsfile

## sh

How to escape double quotes:

```grovy
sh """ echo \\"someTest\\" """
```

## Environment variables

Basic environments block:

```grovy
environment {
  TARGET_ENV = "dev"
}
```

Accessing an env variable:

```grovy
steps {
  echo "TARGET_ENV = ${env.TARGET_ENV}"

  script {
    env.TARGET_ENV = "test"
  }
  
  echo "TARGET_ENV = ${env.TARGET_ENV}"

  withEnv(["TARGET_ENV=prod"]) {
    echo "TARGET_ENV = ${env.TARGET_ENV}"
  }
}
```

Set the value of an env varible using a `sh` command output:

```grovy
environment {
  DATE = sh(returnStdout: true, script: ''' date --rfc-3339=seconds | sed 's/ /T/' ''').trim()
}
```
