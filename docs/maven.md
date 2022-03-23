# Maven

## Basic actions

Builds the project and installs the resulting artifact into the local Maven repository:

```bash
mvn install
```

Clears the target directory and builds the project and installs the resulting artifact into the local Maven repository:

```bash
mvn clean install
```

Clears the target directory, builds the project without running unit tests and installs the resulting artifact into the local Maven repository:

```bash
mvn clean install -Dmaven.test.skip=true
```

Builds the project and packages the resulting JAR file into the target directory:

```bash
mvn package
```

Clears the target directory, builds the project and packages the resulting JAR file into the target directory:

```bash
mvn clean package
```

Clears the target directory, builds the project and packages the resulting JAR file into the target directory without running the unit tests during the build:

```bash
mvn clean package -Dmaven.test.skip=true
```

## Test management

Runs all integration tests:

```bash
mvn verify
```

Cleans the target directory and runs all integration tests:

```bash
mvn clean verify
```

## Dependency management

Cleans project and copies dependencies from remote Maven repositories to the local Maven repository:

```bash
mvn clean dependency:copy-dependencies
```

Prints out the dependency tree:

```bash
mvn dependency:tree -Dverbose
```

Prints out the classpath needed to run:

```bash
mvn dependency:build-classpath
```

## Thanks

Thanks to Jakob Jenkov for his work. Most of the info's on this page come from [here](https://jenkov.com/tutorials/maven/maven-commands.html)
